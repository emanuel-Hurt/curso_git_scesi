# CURSO GIT

**propietario de este documento: Emanuel Hurtado Castro**

## Primera Clase
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
Se debe descargar el instaldor de git bash, como indica en la página de git.
Posteriormente a ejecutar el instaldor podemos abrir la aplicación de Git bash y realizar las configuraciones básicas vistas anteriormente. 

# Segunda Clase

## Los estados de GIT
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

Crear el punto de guardado: `git commit -m "mensaje descriptivo"`. Crea el punto de guardad con los archivos que están en el staged area. Para ver el punto de guardado: `git log` o mas resumido: `git log --oneline`. 

¿Qué tal si quiero deshacer el último commit? `git reset --soft HEAD~1` 

### Buenas Prácticas
Commit atómico: cada que agregas UNA función nueva, cambios cortos, simples, una tarea enorme se puede divider en minitareas, de esas debes subir commits.

Escribe buenos commits: 
- Deben ser descriptivos y con verbos imperativos (eliminar, agregar, remover, etc.).
- No uses punto final y puntos suspensivos en tus mensajes.
- Usa como máximo 50 caracteres para explicar tu commit.
- Usa un prefijo para tus commits: `git commit -m "tipo de comit: descripción"`. Para el trabajo individual usar el prefijo docs

¿qué pasa si mi commit es tan grande que no lo puedo separar en distintos commits? Solución: `git commit` este comando abre el editor de texto predefinido, escribe allí con la siguiente estructura: 

prefijo: Titulo de commit
Cuerpo que describe tu commit


