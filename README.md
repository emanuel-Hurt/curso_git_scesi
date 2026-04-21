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
