# CURSO GIT

**propietario de este documento: Emanuel Hurtado Castro**
**Email:** emanuel.hurtado.cast@gmail.com

## PRIMERA CLASE
### ¿Qué es GIT?
Es un sistema de versiones distribuido, nos permite guardar archivos y sus versiones de manera local.
Sistema de versiones: porque permite guardar archivos y las versiones de estos.
Distribuido: porque permite que otros colaboren en un determinado proyecto.

### ¿Cómo nacio GIT?
Linus Torvals es el padre de Linux. El y su equipo se encontraban trabajando en un proyecto. Para versionar este proyecto la herramienta que usaron fue BitKeeper, herramienta de uso privativo, no permitia usar otras herramientas similares. BitKeeper encontro al equipo de Linus usando otras herramientas y les quitó el acceso a sus repositorios, esta fue la causa por la que Torvals decidio crear GIT.

### ¿Cómo instalar GIT?
Los pasos a seguir para la instalación se encuentran detallados en la página de git.

Caso Linux Ubuntu:
1ro usar el comando `apt-get install git`
2do corroborar que se instaló correctamente: `git --version`
3ro configuraciones básicas:
`git config --global user.name [nombre-a-usar]`
`git config --global user.email [email-a-usar]`
4to verificar las configuraciones realizadas: `git config --list`

Caso Windows:
Se debe descargar el instaldor de git bash, como indica en la [página de git](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Instalaci%C3%B3n-de-Git).  
Posteriormente a ejecutar el instaldor podemos abrir la aplicación de Git bash y realizar las configuraciones básicas vistas anteriormente. 

## SEGUNDA CLASE

### Los estados de GIT
Luego de hacer `git init` GIT maneja los siguientes tres estados para los archivos:

1. Directorio de trabajo  Primer estado, creo modifico o elimino los ficheros, git aún no lo tiene asegurado.
2. Stage Area, es el area de espera
3. Repositorio Local (commited), va a crear el punto de guardado con los archivos que estaban en el stage area.

En el primer estado git solo observa tus archivos y los cataloga:
- Untracked: sin seguimiento, git no tenia idea de su existencia, es algo nuevo que se creo.
- Modified: cuando git ya conocia el archivo y nota que le hicieron cambios.

`git status` nos permite ver el estado de nuestros archivos.

`git restore [nombre_archivo]` , para descartar el cambio y volver a como estaba el archivo, **OJO: borra físicamente el cambio en el archivo**. Con git restore también podemos recuperar archivos borrados.

.gitignore es el archivo cuya finalidad es contener los nombres de los archivos o directorios que no quiero subir al repositorio. Prueba: si pongo `git status` ya no debe mostrar los archivos nombrados en el archivo gitignore, porque git ya no los observa.

Stage Area (preparado): llegas aquí con `git add [nombre_archivo]` o `git add .` Seleccionar los archivos cuyos cambios queremos que se guarden.

Quitar el archivo de Staged area: `git restore --staged [nombre_archivo]`

Crear el punto de guardado: `git commit -m "mensaje descriptivo"`. Crea el punto de guardado con los archivos que están en el staged area. Para ver el punto de guardado: `git log` o mas resumido: `git log --oneline`. 

¿Qué tal si quiero deshacer el último commit? `git reset --soft HEAD~1` Este comando debe ser usado con mucho cuidado.

### Buenas Prácticas
Commit atómico: cada que agregas UNA FUNCIÓN NUEVA, cambios cortos, simples. 
Una tarea enorme se puede divider en minitareas, de esas debes subir commits.

Escribe buenos commits: 
- Deben ser descriptivos y con verbos imperativos (eliminar, agregar, remover, etc.).
- No uses punto final y puntos suspensivos en tus mensajes.
- Usa como máximo 50 caracteres para explicar tu commit.
- Usa un prefijo para tus commits: `git commit -m "tipo de comit: descripción"`. 
Para este trabajo individual usar el prefijo docs

¿qué pasa si mi commit es tan grande que no lo puedo separar en distintos commits? Solución: `git commit` este comando abre el editor de texto predefinido, escribe allí con la siguiente estructura: 

prefijo: Titulo de commit  
- descripción 1
- descripción 2 

## TERCERA CLASE 

### GitHub
Te permite trabajar en equipo. Es la plataforma de desarrollo colaborativo 
más grande del mundo.  
#### Conectar tu repositorio local con GitHub
Vamos a gitHub.com para crear cuenta. Ya con la cuenta creada hacemos lo siguiente:  
1. Configura tu identidad (si no lo has hecho), puedes ver esta parte en la sección 
¿Cómo instalar GIT?
2. Generar llave SSH. La forma más fluida de trabajar si que te pida usuario y contraseña 
a cada rato es usar **llaves SSH**. Ejecuta el siguiente comando:  
`ssh-keygen -t ed25519 -C "tuEmail"`  
3. Copia la llave generada en GitHub:  
- `cat ~/.ssh/id_ed25519.pub` (y copias el texto que sale) 
- Pégala en GitHub: Ve a tu GitHub -> Settings -> SSH and GPG keys -> New SSH key 
ponle un nombre (ej. "Mi laptop") y pega el código. 
4. Probar la conexión: `ssh -T git@github.com` si todo está bien, verás un mensaje de 
exito.  
#### ¿Cómo subir un proyecto nuevo?
Una vez configurado lo anterior, el flujo para subir tus proyectos locales es este:  
1. En GitHub: Dale al botón "+" -> New repository. Ponle nombre y no selecciones nada de 
"README" o "License" (queremos el repo vacío).  
2. En tu terminal (dentro de tu carpeta de proyecto): 
    1. `git init` si aún no tiene git local.
    2. `git add .` 
    3. `git commit -m "Mi primer commit"` 
    4. Conecta con el servidor, asegurate de usar la pestaña SSH en GitHub para copiar 
    este link. `git remote add origin git@github.com:TU_USUARIO/NOMBRE_REPO.git` 
    5. Sube el código: `git push -u origin main`  
**El dia a dia** a partir de ahora, cada vez que hagas cambios, solo necesitas:
1. `git add .`
2. `git commit -m "mensaje"`
3. `git push` Y listo, ya está en la nube.  
**OJO** si clonas el proyecto con https luego no podras realizar subidas 
aunque vuelvas generar la llave SSH no lograras subir tus cambios. 
#### Portafolio en Git
Si creas un repo con tu nombre de usuario de GIT, gitHub entiende que se 
trata de tu presentación, tu portafolio. Por tanto el README que se creará 
será como tu carta de presentación.  

## CUARTA CLASE
### GIT remote 
 permite gestionar nuestras conexiones con los repositorios 
remotos.
`git remote -v` nos permite ver las URLs exactas donde apunta nuestro repo.
`git remote add <apodo> "url"` - Vincula nuestro repo local con uno en la nube. 
`git remote set-url <apodo> "url"` - cambia la url donde apunta nuestro 
repositorio.  
Nota: <apodo> es un alias que le damos a la url de un repositorio remoto. 
Cuando ejecutas `git remote add origin <URL>`, le estas diciendo a Git: En lugar 
de hacerme escribir toda esta URL larga cada vez que quiera subir o bajar código, 
permíteme referirme a ella simplemente como **origin**.
### Múltiples SSH  
¿Qué pasa si necesitamos tener múltiples cuentas? Debemos generar más de una 
llave SSH, pues esta nos da acceso a cada cuenta.  
**Paso 1:** generamos la llave: `ssh-keygen -t ed25519 -C "" -f ~/.ssh <nombre llave>`     
Nota: al momento de generar tu primera llave ssh se crea también la carpeta .ssh  
Nota: el archivo .config debes crearlo en la carpeta .ssh, este ayuda a manejar 
múltiples cuentas. 

### Git checkout 
Es el comando que nos permite desplazarnos visualmente atrás, ver lo 
que hicimos en nuestros anteriores commits. Que el puntero apunte a 
otro commit y ver lo que había entonces.  
## QUINTA CLASE 
### Ramas 
Son versiones de nuestra rama main. En las cuales podemos trabajar sin afectar la rama 
main. Permite trabajar en equipo.  
#### Comandos
`git branch` nos muestra las ramas que tenemos.  
`git branch <nombre_rama>` nos permite crear una nueva rama.  
`git branch -D <ramaEjemplo>` para eliminar la rama ramaEjemplo, tienes que estar fuera 
de la rama rama_ejemplo para eliminarla.  
`git checkout <ramaTres>` con esto me voy a la rama ramaTres.  
`git checkout -b <nuevaRama>` crea nuevaRama y me mueve a esa rama.
`git switch <ramaCuatro>` nos permite cambiar entre ramas.  
`git switch -c <ramaCinco>`crea la rama ramaCinco y me mueve allí.  
OJo con git restore ¿qué hace?  
### Git Flow 
Es un flujo de trabajo, un marco de trabajo porque tiene reglas establecidas, un estandar 
para entendernos en equipo.  
#### Ramas
- rama main, aquí va el código que sabemos que funciona. Código en producción.
- develop, es la rama de preproducción, ya casi entrando a producción.  
Cuando quiero crear una nueva feature debo crear una rama de apoyo: 
    - rama feature, por ejemplo, deseo agregar la funcionalidad sumar, entonces debo crear 
    la rama feature/add-plus-function: 
    `git checkout -b feature/add-plus-function`   
    Todo lo que voy a hacer para esta función la trabajo en esta rama.  
    Debo crear una rama feature por cada nueva función que vaya a implementar.  
    Luego de fusionar la funcionalidad de esta rama con la rama dev, ELMINAR LA RAMA feature. 
    - rama release, se crea para hacer los testing. 
    - rama hotfits, es una derivada de la MAIN, para solucionar de manera rápida un bug 
    en el main. 
## SEXTA CLASE 
Continuamos viendo cómo trabajar de manera grupal.  
### git merge 
Es el comando que nos permite fusionar ramas.    
1ro nos vamos a la rama donde queremos colocar los cambios, movernos a la rama dev  
2do `git fetch` mira las ramas de develop remota en busca de cambios y te INFORMA si existen cambios.  
3ro `git pull origin develop` trae los cambios develop remoto a tu máquina local, 
es la manera de estar actualizado con lo que hizo el equipo.  
4to `git merge --no-ff <mi_rama>` (no fast forward) es para que mantenga el registro de los logs.
Nota: dejá el mensaje del merge tal como está.  
5to `gti branch -D <mi_rama>` Borramos la rama, porque ya no vamos a hacer nada mas allí.  
### git merge conflictivo 
Cuando distintos autores cambiaron el mismo archivo.  
Abres tu editor de código, verás marcado las secciones confictivas, la idea es que veas con 
que quedarte, pero debes eliminar los símbolos que pone git en el archivo.  

Otro conflicto: Cuando alguien ya subio sus cambios y tu vas a subir recién tus cambios en el 
mismo archivo.  

Otro conflicto: Si tienes tu rama local con actualizaciones del remoto del inicio de los tiempos, 
mejor obten los cambios, haz merge en tu local, resuelve los problemas y luego sube al remoto.  

Nota: Si el repo no te pertenece debes hacer push -u ... la primera vez  

El trabajo grupal es hasta el sábado 2 de mayo 21:00; 3 pts extra por hacer logo para el grupo en el 
README.

## SÉPTIMA CLASE 
Confiamos en que la persona que va a hacer el merge sabe lo que va a hacer y es comunicativo, esto es 
un error.  
¿Cómo reducir estos riesgos? Obligar a que realice el flujo del pull request. Nos permite cuando está 
fucionando ramas, permitir aprobar dicha intesión de pull.  
Flujo:  
1ro Como anfitrión debemos configurar restricciones a las ramas, entre ellas el pullrequest, el número 
de votos para validar.  

Nota: ¿qué hace .gitkeep? 

## OCTAVA CLASE 
`git stash commit -m "commit momentaneo"` -> guarda cambios sin hacer commit, esto permite 
que te cambies de rama por ejemplo. 
`git stash list` te muestra la lista de git stash
`git stash pop` te trae todo

`git diff` con este comando ves los cambios realizados en tu directorio de trabajo que aún 
no has añadido al area de preparación.
`git diff <rama1> <rama2>` para comparar dos ramas. 
`git diff <archivo>` cuando el archivo no está en el staged area. Muestra las diferencias de 
ese archivo con su versión anterior más reciente. 
`git diff --staged .` muestra dotos los cambios que ya has añadido al área de preparación. 
`git diff --staged <archivo>` cuando el archivo está en el staged area. Muestra las diferencias 
del archivo con su versión anterior más reciente. 
