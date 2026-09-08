# scpq-repo

Hosts client-facing Engagement Decks exported from the SCPQ Desk tool, served as
static pages via GitHub Pages.

**Live site root:** `https://chrisdebayle.github.io/scpq-repo/`
(the root page is a neutral placeholder — it has no client info and no links.
Folder names are the only way in, so they're the real privacy boundary.)

## Adding a new proposal

1. In SCPQ Desk, open the deal, set a password on it *if this one should be gated*
   (your call, case by case), then click **Export as HTML**. It downloads as
   `index.html`.
2. Create a new folder here named `<company>-<contact>-<random-suffix>`, all
   lowercase, hyphen-separated, e.g. `acmeco-jane-doe-a1b2c3`.
   - Generate the random suffix with `openssl rand -hex 3` (6 hex characters) —
     it's what keeps the folder unguessable, since the repo itself is public.
   - Don't reuse a slug across two different deals, even if the company repeats.
3. Drop the exported `index.html` into that folder.
4. Commit and push to `main`. GitHub Pages serves it automatically at:
   `https://chrisdebayle.github.io/scpq-repo/<folder-name>/`
5. Send that link (and the password, separately, if the deck is gated) to the
   prospect.

## Why this structure

- Each proposal is fully isolated in its own folder — no shared state, no risk
  of one client's deck overwriting another's.
- The repo is public (needed for GitHub Pages on the free plan), so the random
  suffix in each folder name is the thing that keeps a proposal from being
  stumbled onto. The password gate (when used) is the real protection for
  the content itself; the folder name is just what keeps it from being
  guessed or crawled.
- Nothing at the repo root ever names a client, so browsing to the bare site
  root reveals nothing.
