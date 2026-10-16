# How it works

*(Español: [HOW-IT-WORKS.es.md](HOW-IT-WORKS.es.md))*

## Whose work this is

The port is [`dhakaaas1/spaghettikart-xbox`](https://github.com/dhakaaas1/spaghettikart-xbox), a
fork of [SpaghettiKart](https://github.com/HarbourMasters/SpaghettiKart). Reading that fork is how
you learn how the port works, and **neither it nor SpaghettiKart has a license**, so this repository
reproduces nothing of either.

## The one technically interesting thing

Every other libultraship port in this family draws through **Mesa** on the console. This one goes
through **DX11**, which is the backend libultraship has for Windows and which turns out to work
inside an AppContainer. That is worth knowing if you are porting another libultraship game: there is
a second path, and it is shorter.

## What repackaging with your own identity changes

A package carries a publisher and a name. Replacing them with yours does two things that matter on a
console in Developer Mode:

- the console has to trust the **signature**, and a certificate you made yourself is one it will
  accept while a stranger's is not;
- the **package family** — name plus publisher — is what the console hangs the app's data folder
  off. Change it later and the game is, as far as the console is concerned, a different game with an
  empty save folder, while the old one stays installed.

So: pick the name once, sign with your own certificate, and keep both.

## What the console does that a desktop does not

Four things, all of which look like a broken build: it will not replace a package with another of
the same version; the app's data folder does not exist until the app has run once; files uploaded
inside a `.zip` come out unreadable to the AppContainer; and with no user signed in, a package
installs and then does nothing. [`INSTALL.md`](INSTALL.md) has them as a table with what to do.
