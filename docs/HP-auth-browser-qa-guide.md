# Auth browser QA guide — test step by step in your browser

This is a **beginner-friendly, hands-on checklist** for testing the new login
system ("backend v2 auth"): register → verify email → login → session → logout →
password reset/change → Device Activity → route protection → Google sign-in.

You test **only with a web browser**. You do **not** need Postman, curl, or any
coding. You do the stations **in order, one at a time** — each station builds on
the one before it.

---

## Part 0 — Read this first (5 rules)

1. **Only use the frontend address:** `http://localhost:11000` (never the backend
   address).
2. **If you open a backend link** like `http://localhost:13000/api/v2/auth/me` you
   will see `401`. **That is correct**, not a bug. The backend only answers the
   frontend, never the browser directly.
3. **HTTP `200` is not "success".** Success = what you **see** (a message, a
   redirect, the list contents). A request can return `200` and still fail.
4. **Go one Station at a time.** Finish a Station, note PASS/FAIL, then move on. If
   a Station fails, stop screwing around further and report it (some later stations
   depend on it).
5. **Hide secrets before sharing** anything: passwords, 6-digit codes, cookie
   values, tokens.

### Words used in this guide

- **Toast** — the small message that pops up (top-center) after an action.
- **BFF** — the frontend's own server that talks to the backend. You never see it;
  it keeps every backend token away from the browser.
- **Session** — "you are logged in". It is stored in a cookie named
  `hablu-session-dev` (locally), which JavaScript **cannot read**.
- **Station** — one small chunk of the test track, built around one button/API.

### Symbols you will see in every Station

| Symbol | Meaning |
|---|---|
| 🗣️ | What this does, in plain words |
| 🔌 | The backend API behind the button (for reference) |
| 📋 | What you must finish first |
| ▶️ | The exact steps to do |
| ✅ | What a **pass** looks like |
| ⚠️ | An extra **edge / failure** case to also try |
| 📸 | What to screenshot as evidence |
| ☐ | Result boxes: **PASS / FAIL / BLOCKED** |

### What is **not** in scope (do **not** report as bugs)

- **GitHub sign-in** — v2 supports **Google only**. In v2 the GitHub button is
  hidden; the old (non-v2) GitHub button is disabled on purpose.
- **Google sign-in availability** — the Google flow is wired but **off** unless the
  developer enables it (`AUTH_OAUTH_ENABLED=true` on the backend, plus the Google
  client + redirect URI + `V2_OAUTH_STATE_SECRET` on the frontend). If the Google
  button is missing or greyed out, that is the **feature gate**, not a bug. Confirm
  with the developer before **Station 17**.
- **Legacy dashboard / business data** — the bridge that feeds old dashboard/business
  APIs is not built yet. Only report **auth** behaviour.
- **Real client-IP rate limiting** — the global IP backstops stay off
  (`AUTH_RATE_LIMIT_ENABLED=false`). Per-endpoint limits still apply.
- **Deployed / production behaviour** — this pass is for the **local** setup only.

### The buttons you are testing (quick map)

| # | What you do | Page | Behind the button (API) |
|---|---|---|---|
| 1 | Register (name + email) | `/register` | `POST /api/v2/auth/register` |
| 2 | Verify email (code + set password) | `/verify-user` | `POST /api/v2/auth/verify-email` |
| 3 | Resend verification code | `/verify-user` | `POST /api/v2/auth/resend-verification` |
| 4 | Login | `/login` | `POST /api/v2/auth/login` |
| 5 | Current account (shows on every page) | any page | `GET /api/v2/auth/me` |
| 6 | Token refresh (automatic) | after ~15 min | `POST /api/v2/auth/refresh` |
| 7 | Logout | navbar | `POST /api/v2/auth/logout` |
| 8 | Forgot password | `/forgot-password` | `POST /api/v2/auth/forgot-password` |
| 9 | Reset password | `/forgot-password` (step 3) | `POST /api/v2/auth/reset-password` |
| 10 | Change password (signed in) | `/profile` → Change Password | `POST /api/v2/auth/change-password` |
| 11 | Device Activity (list) | `/profile` | `GET /api/v2/auth/sessions` |
| 12 | Sign out another device | `/profile` | `POST /api/v2/auth/sessions/:id/revoke` |
| 13 | Continue with Google (sign in) | `/login` → Google | `POST /api/v2/auth/oauth-exchange` |
| 14 | Link Google (signed in, same email) | `/profile` → Linked Accounts | `POST /api/v2/auth/oauth-link` |
| 15 | Linked accounts (list) | `/profile` → Linked Accounts | `GET /api/v2/auth/oauth-identities` |
| 16 | Unlink Google | `/profile` → Linked Accounts | `POST /api/v2/auth/oauth-unlink` |

---

## Part 1 — Setup (do this once, before Station 1)

### 1.1 Ask the developer to confirm

Before you start, the developer must confirm:

- Backend and frontend are running (see 1.2).
- Email sending works (you will need real codes).
- For **Station 17 (Google)**: `AUTH_OAUTH_ENABLED=true`, the Google client +
  redirect URI are set, and `V2_OAUTH_STATE_SECRET` is set.

### 1.2 Check both apps are alive

| App | Address | What you should see |
|---|---|---|
| Frontend (Next.js) | `http://localhost:11000` | the `/login` page opens, no server error |
| Backend (NestJS) | `http://localhost:13000/health/ready` | `"mongo":"up"` and `"redis":"up"` |

- If `/login` shows a server error like **"Missing required server-only v2 auth
  env"**, the frontend is not fully configured. Tell the developer — **not** a
  product bug.
- If the backend health link does not show `up` for both, tell the developer.

### 1.3 Set up your browser

Use a **Chromium-based browser** (Chrome / Edge / Brave). Then:

1. Press **F12** to open DevTools.
2. Go to the **Network** tab → tick **Preserve log** and **Disable cache**.
3. Go to the **Application** tab → you will use **Cookies** and
   **Local/Session Storage** later.
4. Leave the **Console** tab open (watch for red errors).
5. Keep **one incognito window** ready (for "another device" checks).

### 1.4 Prepare your test data

| Item | Example / rule |
|---|---|
| **Account A** (main) | a **brand-new** email you can open (not a migrated old one) |
| **Account B** (optional) | a second email you own (for "another device") |
| **Good password** | 6–128 characters, not a common password |
| **Wrong password** | e.g. `not-the-password` |
| **Invalid code** | six digits, e.g. `000000` |
| **Re-used code** | a code you already used once |

> Letting codes arrive: keep your inbox open in a second browser tab. If a code
> email never arrives, check spam, then report **BLOCKED** with the time — that is
> usually an email/SMTP environment problem, not a UI bug.

### 1.5 The rules that decide PASS/FAIL (so your expectations are exact)

- **Codes** (verify & reset): 6 digits · valid **600 s** · **5** tries ·
  **300 s** resend cooldown · max **3 sends per email per hour**.
- **Password**: **6–128** characters (not trimmed); a common-password blocklist
  applies.
- **Session**: access token **900 s**; idle **7 days**; absolute **30 days**; max
  **10** active sessions. Login needs a **verified** email.
- **No account-existence leak**: register / resend / forgot-password always give the
  same neutral answer, whether or not the email exists.
- **Cookie**: `hablu-session-dev` locally (`__Host-hablu-session` in production);
  `HttpOnly`, `SameSite=Lax`, `Path=/`, `Secure` only in production. The browser
  **never** holds a backend token.

### 1.6 You are ready when…

- Both apps are up, DevTools is set, and you have Account A's email ready.

---

## Part 2 — The test track (do the Stations in order)

How each Station is written:

```text
🗣️ What it does        (plain words)          ── the button/page
🔌 API behind it       (for reference)
📋 Before you start    (which earlier Station it needs)
▶️ Steps               (numbered, exact)
✅ Pass looks like      (what you should see)
⚠️ Also try            (the failure/abuse case)
📸 Screenshot this
☐ Result:  PASS / FAIL / BLOCKED
```

---

### Station 1 — Open the pages while logged out  (A1)

🗣️ The public auth pages should open cleanly when nobody is logged in.

🔌 Frontend pages only (no API call).

📋 Before you start: fresh **incognito window** (so you are logged out).

▶️ Steps
1. Open `http://localhost:11000/login`.
2. Open `http://localhost:11000/register`.
3. Open `http://localhost:11000/forgot-password`.

✅ Pass looks like
- All three pages open.
- Text is in English.
- No stuck spinner, no error screen, no empty page.

⚠️ Also try: reload each page once — it should still open.

📸 Screenshot this: each page open, no error.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 2 — Register a new account  (A2 – A6)

🗣️ Create a new account with **name + email only** (no password yet — the password
is set later, after email verification).

🔌 `POST /api/v2/auth/register`

📋 Before you start: Station 1 done; Account A email ready.

▶️ Steps
1. Open `/register`.
2. Press the submit button **without typing anything**.
3. Type an **invalid email** (e.g. `abc`) and submit.
4. Confirm the **form shape**: it must have **Name** and **Email** only, **no
   password field**, and a note like *"You will set your password after verifying
   your email."* **(A3)**
5. Now enter **Account A** name + email and click **Create an account**. **(A4)**
6. **Duplicate check (A5):** register the **same** email again.

✅ Pass looks like
- Steps 2–3: clear field errors; you do not advance.
- Step 4: name + email only, no password.
- Step 5: a loading state; a **success toast**; redirect to
  `/verify-user?email=…`; a verification email arrives shortly; **you are NOT
  logged in**.
- Step 6: no crash; a neutral "if eligible…" acknowledgement that does **not**
  confirm whether the account exists; you stay on the page.

⚠️ Also try (register failure — A6, optional): ask the developer to **stop the
backend**, then submit. You should see an **error**, **no** success toast, **no**
redirect, your typed text kept, and it works again after the backend restarts.

📸 Screenshot this: the success toast + the `/verify-user` page; and the duplicate
(the neutral message).

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 3 — Resend the verification code  (A12 – A14)

🗣️ Ask for a fresh verification code; it is rate-limited with a countdown.

🔌 `POST /api/v2/auth/resend-verification`

📋 Before you start: Station 2 done; you are on `/verify-user`.

▶️ Steps
1. Press **Resend** once and watch the button. **(A12)**
2. Note the countdown (`Resend (m:ss)`) and press Resend again immediately.
3. While the countdown is running, **reload** the page. **(A13)**
4. Wait for the countdown to finish, then press Resend.
5. Open `/verify-user` **with no `?email=`** in the URL. **(A14)**

✅ Pass looks like
- Step 1: while sending it shows a **spinner + "Sending…"**; then the countdown
  **restarts** and a **new** code arrives.
- Step 2: button is **disabled** during the countdown.
- Step 3: the countdown **continues** where it was (it does **not** jump back to
  `5:00`).
- Step 5: message **"No email to verify. Please register again."**

⚠️ Also try: send codes rapidly to trigger the **3-per-hour** cap; you should see a
clear English message and recovery after the window.

📸 Screenshot this: the `Resend (m:ss)` countdown, and the reload keeping the time.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 4 — Verify your email and set a password  (A7 – A11)

🗣️ Enter the emailed code **and** choose a password. This completes the account.

🔌 `POST /api/v2/auth/verify-email`

📋 Before you start: Station 3 done; the latest code is in your inbox.

▶️ Steps
1. Enter an **incomplete** code and press **Next**. **(A7)**
2. Enter a **wrong** six-digit code, then a **valid password**, and click **Verify &
   set password**. **(A8)**
3. Enter a **correct-shape code** (wrong is fine here) + a password **shorter than 6
   characters**. **(A9)**
4. Enter the **latest real code** + a **valid password** and submit. **(A10)**
5. Try to **re-use** that same code once more. **(A11)**

✅ Pass looks like
- Step 1: **"Enter the 6-digit code."**; you do not advance.
- Step 2: error *"The code is invalid or has expired…"*; **no** `/login` redirect;
  you return to the **code step**, cleared; you can retry.
- Step 3: the password policy message; you **stay on the password step** to edit.
- Step 4: success toast *"Your account has been verified. You can now log in."*;
  redirect to `/login`; **no auto-login**.
- Step 5: verification does **not** complete again (treated as invalid/expired).

📸 Screenshot this: the success toast + the `/login` redirect.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 5 — Log in with email + password  (B1 – B6)

🗣️ Sign in, and check the wrong-input and redirect behaviour.

🔌 `POST /api/v2/auth/login`

📋 Before you start: Station 4 done (Account A is verified).

▶️ Steps
1. On `/login`, enter Account A email + **wrong password**. **(B1)**
2. Enter a **non-existent** email + any password. **(B2)**
3. **Unverified check (B3):** register a brand-new account (Station 2) but log in
   **before** verifying.
4. Sign in with the **correct** Account A credentials. **(B4)**
5. **Callback (B5):** sign out, open `/profile`. You are sent to `/login`; now log
   in.
6. **Persistence (B6):** reload; then open a **second tab** (same window) and visit
   `/profile`.

✅ Pass looks like
- Step 1: an error; you stay on `/login`; **your typed text is kept**; no session.
- Step 2: a message **no stronger** than step 1 (never says "email not found").
- Step 3: login is **refused** (unverified) — no session.
- Step 4: success toast; redirect to **`/`**; the navbar/profile shows you are
  signed in.
- Step 5: after login you land on the **internal** page you wanted (`/profile`).
- Step 6: you stay signed in in both.

⚠️ Also try (security): a crafted external `callbackUrl` (e.g. `https://evil.example`)
must **not** send you off-site.

📸 Screenshot this: the toast + `/` after login; the callback landing on `/profile`.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 6 — Your account appears on every page  (/me)  (B4/B6 support)

🗣️ Once signed in, the app knows who you are on every page.

🔌 `GET /api/v2/auth/me`

📋 Before you start: Station 5 done (signed in).

▶️ Steps
1. Visit `http://localhost:11000/` (home).
2. Visit `/profile`.

✅ Pass looks like
- The navbar / profile area shows **your** identity (name/avatar) — not "Login".
- `/profile` shows **your** data, without asking you to log in again.

⚠️ Also try: open a page in a **new tab** — same result.

📸 Screenshot this: any page showing you are signed in.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 7 — Stay signed in after the token expires  (B7)

🗣️ The access token expires every 15 minutes; the app should silently refresh it.

🔌 `POST /api/v2/auth/refresh`

📋 Before you start: Station 5/6 done (signed in).

▶️ Steps
1. Stay signed in.
2. **Wait more than 15 minutes** (or ask the developer to make the token expire
   quickly).
3. Load `/profile`.

✅ Pass looks like
- You are **still signed in** (the token refreshed automatically).
- No redirect to login; no endless loading.

⚠️ Also try: open two tabs and load `/profile` in both at the same moment — both
should stay signed in (no "flicker to logged-out").

📸 Screenshot this: `/profile` still showing your data after the wait.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 8 — Log out  (C1 – C3)

🗣️ Sign out from the navbar.

🔌 `POST /api/v2/auth/logout`

📋 Before you start: signed in (Station 5).

▶️ Steps
1. Click **Log Out** in the navbar. **(C1)**
2. **Two tabs (C2):** sign in, open two tabs, log out in tab A, then click something
   protected in tab B.
3. After logout, press the browser **Back** button. **(C3)**

✅ Pass looks like
- Step 1: redirect to `/login`; the cookie is cleared; `/profile` now asks for
  login.
- Step 2: tab B's **next protected action is denied**. (A page already drawn may
  still "look" signed in — what matters is the next request.)
- Step 3: no protected data or action succeeds from the stale view.

📸 Screenshot this: `/login` after logout; the denied action in tab B.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 9 — Ask for a password-reset code  (D1 – D2)

🗣️ Request a reset code for an email address.

🔌 `POST /api/v2/auth/forgot-password`

📋 Before you start: signed out.

▶️ Steps
1. Open `/forgot-password`; first submit an **invalid email**, then Account A's
   email. **(D1)**
2. On the code step, click **Change email**. **(D2)**

✅ Pass looks like
- Step 1: invalid input blocked; eligible account gets a code; the acknowledgement
  does **not** reveal whether the account exists; no false success.
- Step 2: returns to the email step; the email field is editable.

📸 Screenshot this: the acknowledgement, and the "Change email" return.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 10 — Reset your password  (D3 – D5)

🗣️ Enter the reset code + a new password.

🔌 `POST /api/v2/auth/reset-password`

📋 Before you start: Station 9 done; the reset code is in your inbox.

▶️ Steps
1. Enter a **wrong** reset code + a valid new password. **(D3)**
2. Enter the **real** code + a valid new password; click **Reset Password**. **(D4)**
3. Keep Account A signed in **in another browser/profile**, then do step 2 from
   here. **(D5)**
4. Try to log in with the **old** password, then the **new** password.

✅ Pass looks like
- Step 1: an error; **no** `/login` redirect; you return to the code step.
- Step 2: success *"Your password has been reset. Please log in again."*; redirect
  to `/login`; the **old** password fails; the **new** works; the code cannot be
  reused.
- Step 3: the other signed-in place is signed out on its next protected action.

📸 Screenshot this: the success toast; old-password fail; new-password success.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 11 — Change your password while signed in  (E1 – E5)

🗣️ Use the Change Password drawer on your profile.

🔌 `POST /api/v2/auth/change-password`

📋 Before you start: signed in (Station 5).

▶️ Steps
1. Go to `/profile` → **Change Password**. **(E1)**
2. Enter a **wrong** current password + a valid new one. **(E2)**
3. Try **empty** fields; then **New ≠ Confirm**. **(E3)**
4. Enter the **correct** current password + a valid new one + matching confirm.
   **(E4)**
5. Inside the drawer, click the **Forgot password?** affordance. **(E5)**

✅ Pass looks like
- Step 1: a drawer titled **Change Password** with **Current / New / Confirm**
  (v2 has **no** email-code step here).
- Step 2: an error; you can retry; **you are not signed out**.
- Step 3: correct validation messages; the password is unchanged.
- Step 4: success *"Your password has been changed. For security, please log in
  again."*; redirect to `/login`; **all** sessions are revoked (the other place is
  signed out); old password fails, new works.
- Step 5: you are signed out and taken to `/forgot-password`.

📸 Screenshot this: the drawer; the success toast + `/login`; the other-session
signed out.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 12 — Device Activity (your sessions)  (F1 – F4)

🗣️ Your profile lists the devices/sessions currently signed in.

🔌 `GET /api/v2/auth/sessions`

📋 Before you start: signed in.

▶️ Steps
1. Go to `/profile`. **(F1)**
2. Look at **your own** row. **(F2)**
3. Sign in with Account A in a **second browser/profile**, then reload `/profile` in
   the first. **(F3)**
4. **(F4, optional)** Confirm you only ever see **your own** sessions.

✅ Pass looks like
- Step 1: a **Device Activity** table: **No. · Device · Browser · IP · Last Active ·
  (action)**; your current session is listed.
- Step 2: the action cell for your own row reads **"This device"** (no sign-out
  button).
- Step 3: **both** sessions appear; only the **other** one has a **Sign out**
  button.
- Step 4: no other user's rows ever appear.

📸 Screenshot this: the table with your session marked "This device".

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 13 — Sign out another device  (G1 – G3)

🗣️ Remove a different device's session from your list.

🔌 `POST /api/v2/auth/sessions/:id/revoke`

📋 Before you start: Station 12 done (two sessions listed).

▶️ Steps
1. In `/profile`, click **Sign out** on the **other** device's row. **(G1)**
2. In the **second** browser, load a protected page. **(G2)**
3. Revoke an already-revoked row (reload and try again if it reappears). **(G3)**

✅ Pass looks like
- Step 1: the button shows a loading state, then **"Signed out"**; the list
  refreshes and that row is **gone**.
- Step 2: the other device is now signed out (sent to login).
- Step 3: no error exposed; the UI stays consistent.

📸 Screenshot this: the row disappearing; the second device logged out.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 14 — Route protection (public vs private)  (H1 – H5)

🗣️ Private pages need login; public pages do not.

🔌 Frontend routing (middleware) — no API call.

📋 Before you start: one **incognito** window (logged out).

▶️ Steps
1. In the incognito window, visit `/profile`, `/dashboard`, `/settings`, `/payment`.
   **(H1)**
2. **Stale cookie (H2):** sign out (or ask the developer to clear the session
   server-side), then reload a private page with the old cookie still present.
3. Visit public pages: `/`, `/about`, `/privacy-policy`, `/terms-&-conditions`,
   `/refund-policy`, and a course page `/courses/<any-slug>`. **(H3)**
4. Open `/courses/any-brand-new-slug`. **(H4)**
5. Open `/login` and `/register` (with a stale/garbage cookie present). **(H5)**

✅ Pass looks like
- Step 1: **none** show protected content; each sends you to `/login`.
- Step 2: you are still sent to login (the stale cookie does **not** keep you in);
  the app clears it.
- Step 3: all open **without** a login redirect.
- Step 4: treated as a public course (opens). A sibling like `/courses-evil` must
  **not** be treated as a course.
- Step 5: the auth pages still **render** (you are not locked out).

📸 Screenshot this: a private page → `/login`; public pages opening.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 15 — Security & privacy in DevTools  (I1 – I5)

🗣️ Confirm the browser holds **no** backend tokens, and limits behave.

🔌 Uses the cookies/responses of the earlier Stations.

📋 Before you start: signed in; DevTools open.

▶️ Steps
1. **Cookie shape (I1):** Application → Cookies → find the session cookie.
2. **No tokens (I2):** check Local Storage, Session Storage and `document.cookie`.
3. **Clean responses (I3):** in Network, inspect the login / refresh / sessions
   responses.
4. **Double-submit (I4):** double-click submit (or press Enter twice) on register,
   login, verify, and resend.
5. **Rate-limit feedback (I5):** trigger a limit (e.g. one extra register in the
   window).

✅ Pass looks like
- Step 1: the session cookie is `HttpOnly`, `SameSite=Lax`, `Path=/`, and `Secure`
  **only** in production.
- Step 2: **no** backend access/refresh token and **no** session handle; the
  `HttpOnly` cookie is unreadable from JS.
- Step 3: no backend token or session handle reaches the browser. (Your typed
  password in the request payload is expected.)
- Step 4: no duplicate or out-of-order action (verify in Network — a disabled
  button alone is not proof).
- Step 5: a clear English message, no auto-retry loop, recovery after the window.

📸 Screenshot this: the cookie showing `HttpOnly`; storage empty of tokens.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 16 — Mobile & keyboard  (J1 – J2)

🗣️ The auth screens work on a small screen and with the keyboard.

🔌 Frontend UI only.

📋 Before you start: none.

▶️ Steps
1. Set the window to ~**375 px** wide; check login, register, verify-user,
   forgot-password, and the change-password drawer. **(J1)**
2. Use **Tab/Enter**, paste into the OTP boxes, and toggle the password eye.
   **(J2)**

✅ Pass looks like
- Step 1: no horizontal scrolling; OTP boxes and buttons stay in view; messages are
  readable.
- Step 2: Tab/Enter work; OTP paste works; the password toggle does **not** submit;
  long errors do not break the layout.

📸 Screenshot this: a small-screen view of one screen.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

### Station 17 — Google sign-in (OAuth)  (K1 – K8)

🗣️ Sign in with Google, auto-link an existing account, and unlink.

🔌 `POST /api/v2/auth/oauth-exchange` (sign-in), `oauth-link` / `oauth-identities`
/ `oauth-unlink` (manage).

📋 Before you start
- The developer confirms OAuth is enabled (see 1.1). If the Google button is
  missing or greyed at `/login`, **stop** — that is the feature gate, not a bug.
- You need **two Google accounts**: one whose email `X` is **not** registered, and
  one whose email matches an existing account `Y`.

> **Auto-link is on purpose (owner decision 2026-10-16).** A Google-verified email
> that already has an account **auto-links (or creates the account) and signs in** —
> no manual step. It is safe because a password here only ever exists **after**
> email verification. Reporting "it linked my existing account automatically" as a
> bug is a **false positive**.

▶️ Steps
1. **First sign-in, new email (K1).** Signed out, click **Continue with Google**,
   choose the **unregistered** Google account.
2. **Existing account, same email (K2).** Signed out, click **Continue with
   Google**, choose the account whose email `Y` already has an account (with or
   without a password).
3. **Manual link (K3, still supported).** Sign in with `Y`'s password → `/profile` →
   **Linked Accounts** → **Link Google** (same email `Y`).
4. **Different email (K4).** Signed in as `Y`, click **Link Google** but choose a
   Google account with a **different** email.
5. **Unlink (K5).** With Google linked **and** a password set, click **Unlink** and
   confirm.
6. **Only sign-in method (K6).** For an account that has **only** Google (no
   password), click **Unlink**.
7. **Gate (K7).** If OAuth is disabled, open `/login`.
8. **Hygiene (K8).** During K1–K3, watch Application → Cookies and the Network tab.

✅ Pass looks like
- K1: you return to the app **signed in** at the default page; name/avatar from
  Google; no password asked.
- K2: you are **signed in** and land on the default page; the Google identity is
  **auto-linked** to your `Y` account. `/profile` → **Linked Accounts** shows
  **"Linked as `Y`"**.
- K3: success toast; the row reads **"Linked as `Y`"**.
- K4: you return to `/profile` with a clear **toast**; **nothing is linked** (row
  stays "Not linked"); the URL's `?error=` is cleared so a refresh does not repeat
  it; no details of the other account are revealed.
- K5: success toast; the row returns to **"Not linked"**; Google sign-in now
  auto-links again (K2).
- K6: refused with **"Set a password before unlinking your only sign-in method."**;
  the account stays linked and you stay signed in.
- K7: the Google button is hidden/disabled, and visiting
  `/api/auth/v2/oauth/google/start` does **not** start a flow (it redirects back
  with an "unavailable" message, never a raw error page).
- K8: a short-lived `hablu-oauth-state` cookie appears during the flow and is
  **gone after** the callback; it is `HttpOnly`. No `id_token`, no Google token,
  and no backend token ever appear in storage, `document.cookie`, or a response
  body. Cancelling on Google's screen returns you to `/login` with a friendly
  message, not a crash.

📸 Screenshot this: signed in after Google; the "Linked as" row; the different-email
toast.

☐ Result: PASS / FAIL / BLOCKED — Notes: ______

---

## Part 3 — Screenshots & reporting

For every **FAIL** or **BLOCKED**, copy this and fill it in:

```text
Test ID (Station):   e.g. Station 3 / A12
What I did:          the exact steps
Expected:            from this guide
Actual:              what happened
Result:              PASS | FAIL | BLOCKED
Evidence:            screenshot(s) + the Network row (status) + the URL + the time
```

Tips:

- Screenshot both the **toast** and the **page** after the action, **plus** the
  Network row (status code).
- If the developer asks, include the backend **request/correlation id**.
- **Hide** passwords, codes, cookie values, and tokens before sharing.

### Results tracker (fill as you go)

| Station | Test IDs | Result | Evidence / Notes |
|---|---|---|---|
| 1 | A1 | | |
| 2 | A2–A6 | | |
| 3 | A12–A14 | | |
| 4 | A7–A11 | | |
| 5 | B1–B6 | | |
| 6 | /me support | | |
| 7 | B7 | | |
| 8 | C1–C3 | | |
| 9 | D1–D2 | | |
| 10 | D3–D5 | | |
| 11 | E1–E5 | | |
| 12 | F1–F4 | | |
| 13 | G1–G3 | | |
| 14 | H1–H5 | | |
| 15 | I1–I5 | | |
| 16 | J1–J2 | | |
| 17 | K1–K8 | | |

---

## Part 4 — If something looks wrong (troubleshooting)

| What you see | Likely cause | What to do |
|---|---|---|
| `/login` server error "Missing required server-only v2 auth env" | frontend env incomplete | ask the developer; not a product bug |
| Direct backend link returns `401` | backend rejects browser callers (by design) | use the frontend address only |
| No code email arrives | email/SMTP or outbox problem | check spam, then file **BLOCKED** |
| Resend button is disabled | 300 s cooldown (or a send in progress) | wait for `Resend (0:00)` |
| Cooldown restarts at `5:00` on reload | **bug** | report it (Station 3, A13) |
| A private page keeps you in after sign-out | **bug** | report it (Station 14, H2) |
| Change password logs you out | expected | all sessions are revoked by design |
| Google button missing/greyed | feature gate off, or env not ready | confirm with the developer (Station 17) |
| Google shows "redirect_uri_mismatch" | the v2 callback URI is not registered in Google Cloud | developer adds the frontend callback URI |

Known limits (not bugs for this pass):

- **Email codes need working email** — no SMTP means no code (environment blocker).
- **Global per-IP backstops are off** (`AUTH_RATE_LIMIT_ENABLED=false`); only
  per-endpoint limits apply.
- **GitHub sign-in is out of scope**, and **Google sign-in runs only when enabled**.
- After logout a page may briefly still *look* signed in — the rule is that the
  **next request** is denied.

---

## Part 5 — Appendix: which button calls which API

| Page / control | Frontend function | Backend endpoint | What it needs |
|---|---|---|---|
| Register form → "Create an account" | `register` | `POST /auth/register` | none (BFF envelope) |
| `/verify-user` → "Verify & set password" | `verifyEmailAction` | `POST /auth/verify-email` | none (BFF envelope) |
| `/verify-user` → "Resend" | `resendVerificationAction` | `POST /auth/resend-verification` | none (BFF envelope) |
| Login form → "Login" | `login` | `POST /auth/login` | none (BFF envelope) |
| Any page (layout) | `currentUser` / `getV2SessionUser` | `GET /auth/me` | access token |
| On token expiry (automatic) | `runWithFreshAccessToken` | `POST /auth/refresh` | refresh credential |
| Navbar → "Log Out" | `logout` | `POST /auth/logout` | session handle |
| `/forgot-password` → "Send reset email" | `reset` | `POST /auth/forgot-password` | none (BFF envelope) |
| `/forgot-password` → "Reset Password" | `newPassword` | `POST /auth/reset-password` | none (BFF envelope) |
| `/profile` → Change Password drawer | `resetPassword` | `POST /auth/change-password` | access token |
| `/profile` → Device Activity list | `getMySessionsV2` | `GET /auth/sessions` | access token |
| `/profile` → row "Sign out" | `revokeSessionAction` | `POST /auth/sessions/:sessionId/revoke` | access token |
| `/login` → "Continue with Google" | route handler `/api/auth/v2/oauth/google/start` → Google → `callback` | `POST /auth/oauth-exchange` | none (BFF envelope) |
| `/profile` → "Link Google" | same BFF callback (signed in) | `POST /auth/oauth-link` | access token |
| `/profile` → Linked Accounts list | `listMyOAuthIdentitiesV2` | `GET /auth/oauth-identities` | access token |
| `/profile` → "Unlink" | `unlinkOAuthAction` | `POST /auth/oauth-unlink` | access token |

> All backend paths are relative to `http://localhost:13000/api/v2`.
