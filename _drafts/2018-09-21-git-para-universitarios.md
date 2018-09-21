Git para universitarios (Parte 1)
=================================

Git es de esas cosas de las que todos hablan y todos asumen que todos los demás saben, pero no. No todos nacen sabiendo Git 😱 y probablemente el mejor momento para aprenderlo es en tus proyectos de la universidad.

¿Qué es Git?
----------
Empecemos en un lugar raro: Git no es [GitHub](http://github.com/), ni es [GitLab](https://gitlab.com), ni es [BitBucket](https://bitbucket.org/) y no necesitas utilizar ninguno de esos servicios para empezar a utilizar Git, aunque si ayuda mucho. Git es una herramienta para hacer _versionamiento_ de tu trabajo.

El versionamiento te permite regresar a versiones previas para arreglar problemas o solo ver cómo ha evolucionado tu proyecto. Piensa en el versionamiento, y Git, como un "Super Save" que te **evita** nombrar tus trabajos como:
- `tarea1.txt`
- y luego `tarea1_final.txt`
- y luego `tarea1_final_elbueno.txt`
- y luego `tarea1_final_noeraelbueno.txt`
- y luego `tarea1_porquenofuncionas.txt`
- y luego....

En vez de eso puedes tener solo un archivo y ver toda su historia.

¿Para qué puedo usar Git?
-------------------------
Git funciona mejor para hacer versionamiento de archivos de _texto plano,_ que son la clase de archivos que puedes hacer en el bloc de notas de windows y TextEdit en MacOS. Eso lo hace muy util para las personas que programan (porque en general el código es texto plano) pero lo puedes utilizar para cualquier otro tipo de archivo.

COMPARTE GIT CON TUS AMIGOS DISEÑADORES, NO SABEN QUE LO NECESITAN PERO SI LO USAN TE LO VAN A AGRADECER SIEMPRE.

La idea es que puedes volver al pasado, y hacer ramas _(branches)_ para explorar otras opciones.
- Tu profesor te pidio que probaras un color diferente? **branch!**
- Quieres intentar empezar de cero sin perder tu trabajo? **branch!**
- Quieres agregar algo al trabajo y no sabes si a tus compañeros les va a gustar? **branch!**

Esta última es una razón buenisima para empezar a utilizar Git. Te permite colaborar con otras personas fácilmente e integrar el trabajo de los demás con tu propio trabajo fácilmente.

¿Cómo empiezo?
--------------
Tienes dos opciones (a) [utilizar una herramienta especial](https://www.gitkraken.com/) (b) hacerlo a mano como los antiguos.

Si quieres usar una herramienta te recomiendo [GitKraken](https://www.gitkraken.com/) es muy simple y claro. Pero en el resto de esta guía nos vamos a concentrar en hacer las cosas a mano, todo lo que vamos a hacer es aplicable a GitKraken, pero hacerlo tu mismo te va a ayudar a entender cómo funciona Git y si te interesa el desarrollo de software, te va a permitir automatizar ciertos procesos.

También te recomiendo ver las guías de [Homebrew y la terminal en MacOS]() o [Bash y la terminal en Windows]() ya que vamos a hacer uso de ella de aquí en adelante.

### Instalando Git

En windows puedes descargar Git directamente, en MacOS también, pero te recomiendo instalarlo con [homewbrew](https://brew.sh/) (Proximamente guía de homebrew y la terminal en MacOS!) y en linux seguramente ya lo tienes instalado, solo acutaliza de acuerdo a tu distribución.

- Windows: https://git-scm.com/download/win
- MacOS: `brew install git`
- Linux: Seguramente ya tienes Git instalando

### Mi primer repo

Un repo (por repositorio) es la carpeta que quieres versionar. Git no versiona archivos individuales, esta pensado para llevar el seguimiento de un proyecto completo, así que crea la carpeta de tu primer repositorio.
