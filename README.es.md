# Mario Kart 64 en la Xbox — la receta, sin código

Cómo llevar la decompilación [SpaghettiKart](https://github.com/HarbourMasters/SpaghettiKart) de
*Mario Kart 64* a una **Xbox Series en modo desarrollador**.

*(English: [README.md](README.md))*

Se juega en dos consolas desde el 2026-09-05.

## Lee esto primero: aquí no hay casi nada, y es a propósito

**El port UWP no es nuestro.** Es [`dhakaaas1/spaghettikart-xbox`](https://github.com/dhakaaas1/spaghettikart-xbox),
el único fork UWP de este juego, y funciona — dibuja con libultraship por **DX11** en vez de Mesa,
que es raro en esta familia.

**Y ni ese fork ni SpaghettiKart tienen licencia.** Así que este repositorio no contiene **ningún
código**: ni un parche, ni una línea de contexto, nada. Lo que tiene es la parte que nadie escribió
—cómo compilar ese fork, cómo darle al paquete tu propia identidad y qué hace la consola que un
escritorio no hace nunca— más el manifiesto con la identidad en blanco, que es nuestro.

Si suena flaco, lo es: la versión honesta de este repositorio *es* flaca. Hacerla gorda significaría
publicar código ajeno sin licencia.

## Qué hay aquí

| | |
|---|---|
| `docs/INSTALL.es.md` | La secuencia, de punta a punta, con el lado de la consola |
| `docs/HOW-IT-WORKS.es.md` | Por qué DX11 y no Mesa, y qué cambia reempaquetar con tu propia identidad |
| `docs/ASSETS.es.md` | Los trece mosaicos y sus medidas |
| `package/Package.appxmanifest` | El manifiesto, con la identidad en `CHANGE-ME` |

## Qué hace falta antes

| | |
|---|---|
| El fork de UWP | [dhakaaas1/spaghettikart-xbox](https://github.com/dhakaaas1/spaghettikart-xbox) |
| Tu propia ROM | El proyecto extrae sus datos él mismo, en tu máquina |
| Visual Studio 2022 | Con la carga de trabajo de C++ para UWP |
| Una Xbox en modo desarrollador | Y un certificado para firmar |

## Lo que hace la consola y no hace un escritorio

- **No reemplaza un paquete por otro de la misma versión**: cada ciclo necesita un número nuevo, o
  instalas y luego ejecutas la compilación vieja.
- La carpeta de datos de la app **no existe hasta que la app ha corrido una vez**.
- Los archivos subidos **dentro de un `.zip`** quedan con permisos que el AppContainer no puede leer.
- **Sin usuario conectado**, un paquete se instala y al abrirlo no pasa nada — que se parece
  exactamente a un paquete roto.

## Créditos y licencia

El port es de **dhakaaas1**, construido sobre **HarbourMasters/SpaghettiKart** y **libultraship**.
Este repositorio es la documentación y el manifiesto en blanco, de **Recompilaciones**, bajo la
[licencia MIT](LICENSE).

*Mario Kart 64* es © Nintendo. Sin afiliación con ellos, ni con Microsoft, ni con los autores de los
proyectos de arriba. El detalle está en [`NOTICE.es.md`](NOTICE.es.md); los titulares de derechos
pueden escribir a **jajdpmail@gmail.com**.
