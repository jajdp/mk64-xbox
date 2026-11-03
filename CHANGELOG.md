# Changelog

All notable changes to this recipe. Dates are `YYYY-MM-DD`.

## 1.0.3 — 2026-11-03

### Changed

- **This repository no longer explains itself by pointing at other repositories of this
  catalogue.** Comments and documentation introduced a decision, a trap or a default as "the same
  as in such-and-such other port of ours" — which asked anyone who came here for this game to go
  and read about a different one first. Each of those comparisons carried a fact that reads better
  stated outright, so that is what is written now.

  What is still cited is everything that is **not** ours: the upstream project, the third-party
  forks the recipe is built on, and the files taken from them under their own license.

## 1.0.2 — 2026-10-20

### Changed

- **The README now says which console this was tested on, and which one it was not.** Everything here
  was built and measured on an **Xbox Series X** in Developer Mode; a **Series S has never been tried**,
  so nothing here says anything about one. The wording used to say "Xbox Series", which reads as if it
  covered both, and it does not.

## 1.0.1 — 2026-10-16

### Fixed

- **`LICENSE`: the explanatory block named the wrong project.** Everything after the MIT text had
  been copied from another repository in this catalogue and never adapted: it said this was a
  derivative of a different project altogether, denied granting rights in a game that is not this
  one, quoted "the 57 lines of the upstream project", and listed folders this repository does not
  have. The MIT grant itself was correct all along, and `NOTICE.md` always had the right figures.
  The block now names SpaghettiKart and its UWP fork, neither of which publishes a license and Mario
  Kart 64, and points at `NOTICE.md` for the measurements instead of repeating a number.

## 1.0.0 — 2026-10-14

First release. The package built this way has been on two Xbox Series X consoles since 2026-09-05.

### Included

- The procedure, end to end, in English and Spanish: building the UWP fork, giving the package your
  own identity, and the console behaviours that look like bugs in your build.
- `package/Package.appxmanifest` with `CHANGE-ME` identity.
- **No code**, on purpose: see `NOTICE.md`.

### Verified before release

The package built this way has been playing on two consoles since 2026-09-05, with the HD texture
pack.

There is nothing else to verify here: this repository publishes documentation and one manifest. The
port is the fork's, and its build is the fork's to verify.
