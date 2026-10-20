# Mario Kart 64 on Xbox — the recipe, with no code

How to get the [SpaghettiKart](https://github.com/HarbourMasters/SpaghettiKart) decompilation of
*Mario Kart 64* onto an **Xbox Series X in Developer Mode**.

*(Español: [README.es.md](README.es.md))*

It has been playing on two consoles since 2026-09-05.

## Which console this was tested on

**An Xbox Series X**, in Developer Mode. Both of the consoles this was built and tested on are Series X,
so that is the only hardware anything claimed here covers.

**A Series S has never been tried — not once.** It is a different machine: less memory available to a
game and a weaker GPU. This may work on one, it may run slower, or it may not start at all; nothing here
has been measured on it. If you run it on a Series S, what you get is not what this README reports, and
none of the numbers here are a promise about that console.

## Read this first: there is almost nothing here, and that is the point

**The UWP port is not ours.** It is [`dhakaaas1/spaghettikart-xbox`](https://github.com/dhakaaas1/spaghettikart-xbox),
the only UWP fork of this game, and it works — it draws through libultraship with **DX11** rather
than Mesa, which is unusual in this family.

**And neither that fork nor SpaghettiKart itself has a license.** So this repository contains **no
code at all**: not a patch, not a context line, nothing. What it has is the part nobody wrote down —
how to build that fork, how to give the package your own identity, and what the console does that a
desktop never does — plus the manifest with its identity blanked, which is ours.

If that sounds thin, it is: the honest version of this repository *is* thin. Publishing a fat one
would mean publishing someone else's unlicensed code.

## What is here

| | |
|---|---|
| `docs/INSTALL.md` | The sequence, end to end, including the console side |
| `docs/HOW-IT-WORKS.md` | Why DX11 and not Mesa, and what repackaging with your own identity changes |
| `docs/ASSETS.md` | The thirteen tiles and their sizes |
| `package/Package.appxmanifest` | The manifest, identity blanked to `CHANGE-ME` |

## What you need first

| | |
|---|---|
| The UWP fork | [dhakaaas1/spaghettikart-xbox](https://github.com/dhakaaas1/spaghettikart-xbox) |
| Your own ROM | The project extracts its assets itself, on your machine |
| Visual Studio 2022 | With the C++ UWP workload |
| An Xbox in Developer Mode | And a certificate to sign with |

## What the console does that a desktop does not

- It **will not replace a package with another of the same version**: every cycle needs a new
  version number, or you install and then run the old build.
- The app's data folder **does not exist until the app has run once**.
- Files uploaded **inside a `.zip`** come out with permissions the AppContainer cannot read.
- **With no user signed in**, a package installs and then does nothing when opened — which looks
  exactly like a broken package.

## Credits and license

The port is **dhakaaas1**'s, built on **HarbourMasters/SpaghettiKart** and **libultraship**. This
repository is the documentation and the blanked manifest, by **Recompilaciones**, under the
[MIT License](LICENSE).

*Mario Kart 64* is © Nintendo. Not affiliated with them, with Microsoft or with the authors of the
projects above. Details in [`NOTICE.md`](NOTICE.md); rights holders can write to
**jajdpmail@gmail.com**.
