# Práctica: Creación y sincronización de repositorios con Git y GitHub

## Datos del estudiante

* **Nombre completo:** Ricardo Balam Reyes Flores
* **Matrícula:** 2630003
* **Nombre de la práctica:** Creación y sincronización de repositorios con Git y GitHub

---

## Objetivo de la práctica

El objetivo de esta práctica fue aprender a crear y administrar un repositorio utilizando Git, además de vincularlo con un repositorio remoto en GitHub.

Durante la práctica se probé el funcionamiento de la sincronización, enviando cambios realizados desde la computadora hacia GitHub y también descargar cambios realizados desde GitHub hacia el repositorio local.

Con esta actividad pude comprender mejor cómo Git permite llevar un control de las modificaciones realizadas en los archivos de un proyecto y cómo GitHub puede utilizarse para almacenar y mantener una copia remota del repositorio.

---

## Descripción del procedimiento realizado

Empecé creando una carpeta para el proyecto y accediedo a ella mediante la PowerShell.

La carpeta utilizada fue:

```text
practica-git-ricardo-reyes
```

Dentro de esta carpeta inicialicé un repositorio local utilizando Git. Posteriormente configuré la rama principal con el nombre `main`.

Creé los archivos:

```text
README.md
datos.txt
```

El archivo `README.md` contiene la información y explicación de la práctica, mientras que `datos.txt` se utilizó para comprobar la sincronización de cambios entre el repositorio local y GitHub.

Una vez creados los archivos, utilicé Git para registrar los cambios mediante un commit. Después creé un repositorio público en GitHub y lo vinculé con mi repositorio local.

Finalmente realicé modificaciones tanto desde GitHub como desde mi computadora para comprobar que la información podía sincronizarse correctamente en ambos sentidos.

---

# 1. Creación del repositorio local

Primero creé la carpeta de la práctica y accedí a ella mediante Powershell.

Para convertir la carpeta en un repositorio de Git utilicé:

```bash
git init
```

Este comando inicializa un nuevo repositorio de Git dentro de la carpeta actual. Al ejecutarlo se crea internamente una carpeta llamada `.git`, en la cual Git almacena la información necesaria para llevar el historial y control de versiones del proyecto.

Después configuré la rama principal con el nombre `main`:

```bash
git branch -M main
```

Este comando permite cambiar el nombre de la rama actual a `main`. 

Posteriormente creé los archivos:

```text
README.md
datos.txt
```

En el archivo `datos.txt` agregué información relacionada con la práctica para posteriormente realizar modificaciones desde GitHub y desde el repositorio local.

---

# 2. Registro de los primeros cambios

Después de crear los archivos verifiqué el estado del repositorio con:

```bash
git status
```

Este comando permite revisar qué archivos han sido creados, modificados o eliminados y también muestra cuáles todavía no han sido preparados para realizar un commit.

Posteriormente agregué todos los archivos al Staging Zone

```bash
git add .
```

El comando `git add .` agrega al área de preparación todos los cambios realizados dentro de la carpeta del proyecto. Esto significa que los archivos quedan listos para ser incluidos en el siguiente commit.

Volví a comprobar el estado utilizando:

```bash
git status
```

En este momento Git mostraba que los archivos ya estaban preparados para realizar el commit.

Después registré los cambios con:

```bash
git commit -m "Primer commit"
```

Un commit funciona como un registro o punto de guardado dentro del historial del proyecto. La opción `-m` permite agregar un mensaje que describe los cambios realizados.

En este caso, el mensaje utilizado fue `"Primer commit"`.

---

# 3. Creación y vinculación del repositorio con GitHub

Después de tener preparado el repositorio local, ingresé a GitHub y creé un nuevo repositorio público con el mismo nombre de la carpeta utilizada para la práctica.

Una vez creado el repositorio copié su dirección URL.

Para vincular el repositorio local con GitHub utilicé:

```bash
git remote add origin https://github.com/BalamReyes/practica-git-Ricardo-Reyes.git
```
El comando `git remote add origin` permite registrar la dirección del repositorio remoto. La palabra `origin` funciona como un nombre o alias que Git utiliza para identificar ese repositorio remoto.

Para comprobar que la conexión se había registrado correctamente utilicé:

```bash
git remote -v
```

Este comando muestra los repositorios remotos vinculados al proyecto y sus respectivas direcciones URL, tanto para descargar como para enviar información.

---

# 4. Sincronización del repositorio local hacia GitHub

Después de vincular los repositorios envié por primera vez el contenido del repositorio local hacia GitHub utilizando:

```bash
git push -u origin main
```

El comando `git push` sirve para enviar los commits del repositorio local hacia el repositorio remoto.

En este caso:

* `origin` representa el repositorio de GitHub.
* `main` representa la rama principal.
* `-u` establece una relación entre la rama `main` local y la rama `main` del repositorio remoto.

Gracias a esto, en futuros envíos fue posible utilizar simplemente:

```bash
git push
```

Después de ejecutar el comando ingresé nuevamente a GitHub y comprobé que los archivos `README.md` y `datos.txt` aparecieran correctamente.

Con esto se comprobó la sincronización:

```text
Repositorio local → GitHub
```

---

# 5. Sincronización de GitHub hacia el repositorio local

Para comprobar la sincronización en el sentido contrario, realicé una modificación directamente desde la página de GitHub.

Abrí el archivo:

```text
datos.txt
```

y agregué la siguiente línea:

```text
Este archivo fue modificado desde GitHub.
```

Después guardé el cambio mediante un commit desde GitHub.

En ese momento el repositorio remoto tenía una modificación que todavía no existía en mi computadora.

Para descargarla regresé a PowerShell y utilicé:

```bash
git pull origin main
```

El comando `git pull` descarga los cambios disponibles en el repositorio remoto y los integra con el repositorio local.

En este comando:

* `origin` indica el repositorio remoto.
* `main` indica la rama de la cual se descargarán los cambios.

Después de ejecutar el comando abrí nuevamente el archivo `datos.txt` y comprobé que aparecía la línea agregada desde GitHub.

De esta forma comprobé la sincronización:

```text
GitHub → Repositorio local
```

---

# 6. Nueva modificación desde el repositorio local

Después de comprobar la descarga de información desde GitHub, realicé una modificación en el archivo `datos.txt`, pero esta vez desde mi computadora.

Agregué la línea:

```text
Este archivo fue modificado desde el repositorio local.
```

Después revisé los cambios realizados con:

```bash
git status
```

Git mostró que el archivo `datos.txt` había sido modificado.

Posteriormente preparé los cambios utilizando:

```bash
git add .
```

Después registré la modificación mediante un nuevo commit:

```bash
git commit -m "Actualización desde repositorio local"
```

Finalmente envié la nueva versión hacia GitHub utilizando:

```bash
git push
```

AL ya haber establecido la relación entre la rama local `main` y la rama remota mediante `git push -u origin main`, ya no fue necesario escribir nuevamente toda la información del repositorio remoto.

Después ingresé a GitHub y comprobé que la modificación realizada desde mi computadora también aparecía en el archivo `datos.txt`.

---

# Comandos de Git utilizados

| Comando                     | Función                                                                                            |
| --------------------------- | -------------------------------------------------------------------------------------------------- |
| `git init`                  | Inicializa un nuevo repositorio de Git en la carpeta actual.                                       |
| `git branch -M main`        | Cambia o establece el nombre de la rama principal como `main`.                                     |
| `git status`                | Muestra el estado actual de los archivos del repositorio.                                          |
| `git add .`                 | Agrega todos los cambios al área de preparación o Staging Area.                                    |
| `git commit -m "mensaje"`   | Registra los cambios preparados dentro del historial del repositorio.                              |
| `git remote add origin URL` | Vincula el repositorio local con un repositorio remoto.                                            |
| `git remote -v`             | Muestra las direcciones de los repositorios remotos configurados.                                  |
| `git push -u origin main`   | Realiza el primer envío de la rama `main` hacia GitHub y establece su relación con la rama remota. |
| `git pull origin main`      | Descarga e integra los cambios realizados en GitHub hacia el repositorio local.                    |
| `git push`                  | Envía los nuevos commits del repositorio local hacia GitHub.                                       |

---

# Archivos contenidos en el repositorio

El repositorio utilizado durante esta práctica contiene principalmente los siguientes archivos:

### `README.md`

Este archivo contiene la documentación de la práctica. En este se describen el objetivo, el procedimiento realizado, los comandos utilizados y el funcionamiento de la sincronización entre Git y GitHub.

### `datos.txt`

Este archivo fue utilizado para realizar las pruebas de modificación y sincronización.

Durante la práctica se modificó primero desde GitHub agregando:

```text
Este archivo fue modificado desde GitHub.
```

Posteriormente se modificó desde el repositorio local agregando:

```text
Este archivo fue modificado desde el repositorio local.
```

Estas modificaciones permitieron comprobar que los cambios podían viajar correctamente en ambos sentidos.

---

# Conclusión

Durante esta práctica aprendí a utilizar las funciones básicas de Git y GitHub para llevar el control de los archivos de un proyecto. Antes de realizarla conocía algunos de los comandos de Git de manera individual, pero con esta actividad pude comprender mejor cómo se relacionan entre ellos dentro de un flujo de trabajo real.

También aprendí la diferencia entre trabajar con un repositorio local y uno remoto. El repositorio local se encuentra almacenado en mi computadora, mientras que el repositorio remoto se encuentra en GitHub y permite mantener una copia del proyecto en línea.

Considero que una de las partes más importantes de la práctica fue comprobar la sincronización en ambos sentidos. Con `git push` pude enviar los cambios realizados desde mi computadora hacia GitHub, mientras que con `git pull` pude descargar los cambios realizados directamente desde GitHub hacia mi computadora.

En conclusión, esta práctica me ayudó a entender que Git no solamente sirve para guardar archivos, sino para llevar un historial organizado de las modificaciones realizadas en un proyecto.