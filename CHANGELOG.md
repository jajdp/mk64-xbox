# Changelog

All notable changes to this recipe. Dates are `YYYY-MM-DD`.

## 1.0.1 — 2026-10-16

### Fixed

- **`LICENSE`: the explanatory block named the wrong project.** Everything after the MIT text had
  been copied from the `dkr-xbox` repository and never adapted: it said this was a derivative of
  Golden Balloon, denied granting rights in Diddy Kong Racing, quoted "the 57 lines of the upstream
  project", and listed folders this repository does not have. The MIT grant itself was correct all
  along, and `NOTICE.md` always had the right figures. The block now names SpaghettiKart and its UWP fork, neither of which publishes a license and
  Mario Kart 64, and points at `NOTICE.md` for the measurements instead of repeating a number.

## 1.0.0 — 2026-10-14

First release. The package built this way has been on two Xbox Series consoles since 2026-09-05.

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
