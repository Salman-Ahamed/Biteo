# FastBite Documentation Structure

## Purpose

This folder is split into two document packs with different jobs.

- `system/` contains the internal working documents used to design, validate, and evolve the product
- `client/` contains cleaned client-facing outputs derived from the system documents

The intent is straightforward:

**system docs are the source material, and client docs are the shareable output.**

## How To Use This Structure

Use `system/` when you need:

- detailed reasoning
- assumptions and open questions
- source notes and evidence boundaries
- technical and operational depth
- validation-oriented working content

Use `client/` when you need:

- directly shareable summaries
- cleaner scope communication
- simpler commercial or product-facing language
- documents that avoid internal research clutter

## Folders

- [system/README.md](./system/README.md): internal source pack, reading order, and document map
- [client/README.md](./client/README.md): shareable output pack for clients and external stakeholders

## Naming Rule

For new documents created from this point onward, use descriptive Title Case names in the style of:

- `High Level Overview of UK Food Delivery System (Pilot MVP).md`

Keep the existing numbered system files as they are, because they already map to the validation prompt set.

## Working Rule

New strategy, validation, architecture, and source-heavy content should be created in `system/` first.

Client-ready documents should then be written or rewritten into `client/` based on the approved system version.
