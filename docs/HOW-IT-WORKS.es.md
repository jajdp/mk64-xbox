# Cómo funciona

*(English: [HOW-IT-WORKS.md](HOW-IT-WORKS.md))*

## De quién es este trabajo

El port es [`dhakaaas1/spaghettikart-xbox`](https://github.com/dhakaaas1/spaghettikart-xbox), un
fork de [SpaghettiKart](https://github.com/HarbourMasters/SpaghettiKart). Leer ese fork es cómo se
aprende cómo funciona el port, y **ni él ni SpaghettiKart tienen licencia**, así que este
repositorio no reproduce nada de ninguno.

## Lo único técnicamente interesante

Todos los demás ports de libultraship de esta familia dibujan por **Mesa** en la consola. Este pasa
por **DX11**, que es el backend que libultraship tiene para Windows y que resulta que funciona
dentro de un AppContainer. Eso conviene saberlo si vas a portar otro juego de libultraship: hay un
segundo camino, y es más corto.

## Qué cambia reempaquetar con tu propia identidad

Un paquete lleva un publicador y un nombre. Cambiarlos por los tuyos hace dos cosas que importan en
una consola en modo desarrollador:

- la consola tiene que confiar en la **firma**, y un certificado hecho por ti es uno que acepta,
  mientras el de un desconocido no lo es;
- la **familia del paquete** —nombre más publicador— es de donde la consola cuelga la carpeta de
  datos de la app. Cámbiala después y el juego es, para la consola, otro juego con la carpeta de
  partidas en blanco, mientras el viejo sigue instalado.

O sea: elige el nombre una vez, firma con tu propio certificado y quédate con los dos.

## Lo que hace la consola y no hace un escritorio

Cuatro cosas, y todas parecen una compilación rota: no reemplaza un paquete por otro de la misma
versión; la carpeta de datos de la app no existe hasta que la app ha corrido una vez; los archivos
subidos dentro de un `.zip` quedan ilegibles para el AppContainer; y sin usuario conectado, un
paquete se instala y luego no hace nada. En [`INSTALL.es.md`](INSTALL.es.md) están en una tabla con
qué hacer.
