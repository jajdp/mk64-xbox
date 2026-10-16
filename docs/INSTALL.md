# Install — from the UWP fork to the game on the console

*(Español: [INSTALL.es.md](INSTALL.es.md))*

There is no code in this repository ([`../NOTICE.md`](../NOTICE.md) says why). This is the
procedure.

## 1. Clone the UWP fork

```powershell
git clone https://github.com/dhakaaas1/spaghettikart-xbox.git C:\mk64
```

It is the only UWP fork of SpaghettiKart, and it draws through libultraship with **DX11** rather
than Mesa — unusual in this family, and the reason it works here.

## 2. Build it, following the fork

Follow the fork's own instructions, with your own ROM: the project extracts the assets itself. Build
for the desktop first if it offers that, because a problem there is not a problem of the console.

## 3. Give the package your own identity

Out of the box the package carries the fork's publisher. Replacing it with yours means the console
treats it as your app, which matters for two reasons: the console has to trust the signature, and
the package family is where your save data lives.

- Put your own `Name` and `Publisher` in the manifest — `package/Package.appxmanifest` in this
  repository is that manifest with both blanked to `CHANGE-ME`.
- `Publisher` must be **exactly** the subject of your signing certificate, `CN=` included.
- Your own thirteen tiles ([`ASSETS.md`](ASSETS.md)); the ones on the real console were made from
  the game's art and are not here.

Create the certificate once, in an **ordinary** PowerShell window:

```powershell
New-SelfSignedCertificate -Type Custom -Subject "CN=<your name>" -KeyUsage DigitalSignature `
  -FriendlyName "<your name> UWP dev" -CertStoreLocation "Cert:\CurrentUser\My" `
  -TextExtension @("2.5.29.37={text}1.3.6.1.5.5.7.3.3", "2.5.29.19={text}")
```

## 4. Install it and feed it its data

Device Portal (`https://<console ip>:11443`, with your Dev Home username and password): **Add** →
the package → with the `Microsoft.VCLibs.140.00` x64 appx as a dependency, and **a user
signed in** on the console.

Then upload the asset archive the build produced to the app's data folder.

## 5. The four console behaviours that look like bugs

| What you see | What it is |
|---|---|
| It installs, you open it, nothing happens | No user signed in on the console |
| It installs but the game is the old build | **The version did not go up.** The console will not replace a package with another of the same version |
| The game cannot find its assets | The data folder **does not exist until the app has run once**: launch it, let it fail, close it, then upload |
| The data is there and the game still cannot read it | It was uploaded inside a `.zip`. Unpacked by the portal, files get permissions the AppContainer cannot open. One file at a time |
