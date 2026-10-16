# Instalación — del fork de UWP al juego en la consola

*(English: [INSTALL.md](INSTALL.md))*

En este repositorio no hay código ([`../NOTICE.es.md`](../NOTICE.es.md) dice por qué). Esto es el
procedimiento.

## 1. Clonar el fork de UWP

```powershell
git clone https://github.com/dhakaaas1/spaghettikart-xbox.git C:\mk64
```

Es el único fork UWP de SpaghettiKart, y dibuja con libultraship por **DX11** en vez de Mesa —raro
en esta familia, y la razón de que aquí funcione—.

## 2. Compilarlo, siguiendo al fork

Sigue las instrucciones del propio fork, con tu ROM: el proyecto extrae los datos él mismo. Compila
primero para escritorio si lo ofrece, porque un problema ahí no es un problema de la consola.

## 3. Darle al paquete tu propia identidad

De fábrica, el paquete lleva el publicador del fork. Cambiarlo por el tuyo hace que la consola lo
trate como tu app, y eso importa por dos cosas: la consola tiene que confiar en la firma, y la
familia del paquete es donde viven tus partidas.

- Pon tu `Name` y tu `Publisher` en el manifiesto — el `package/Package.appxmanifest` de este
  repositorio es ese manifiesto con los dos en `CHANGE-ME`.
- El `Publisher` tiene que ser **exactamente** el sujeto de tu certificado de firma, con el `CN=`.
- Tus propios trece mosaicos ([`ASSETS.es.md`](ASSETS.es.md)); los de la consola de verdad se
  hicieron con el arte del juego y no están aquí.

El certificado se crea una vez, en una ventana de PowerShell **normal**:

```powershell
New-SelfSignedCertificate -Type Custom -Subject "CN=<tu nombre>" -KeyUsage DigitalSignature `
  -FriendlyName "<tu nombre> UWP dev" -CertStoreLocation "Cert:\CurrentUser\My" `
  -TextExtension @("2.5.29.37={text}1.3.6.1.5.5.7.3.3", "2.5.29.19={text}")
```

## 4. Instalarlo y darle sus datos

Device Portal (`https://<ip de la consola>:11443`, con el usuario y la contraseña de Dev Home):
**Add** → el paquete → con el appx de `Microsoft.VCLibs.140.00` para x64 como dependencia, y
**un usuario conectado** en la consola.

Después sube a la carpeta de datos de la app el archivo de datos que produjo la compilación.

## 5. Los cuatro comportamientos de la consola que parecen fallos

| Lo que ves | Qué es |
|---|---|
| Se instala, lo abres y no pasa nada | No hay usuario conectado en la consola |
| Se instala pero el juego es el viejo | **No subió la versión.** La consola no reemplaza un paquete por otro de la misma versión |
| El juego no encuentra sus datos | La carpeta de datos **no existe hasta que la app ha corrido una vez**: láncala, deja que falle, ciérrala y entonces sube |
| Los datos están y el juego sigue sin leerlos | Se subieron dentro de un `.zip`. Extraídos por el portal, quedan con permisos que el AppContainer no abre. De uno en uno |
