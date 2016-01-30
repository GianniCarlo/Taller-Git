# Taller de Git
Antes de empezar se debe tener instalado Git en las computadoras
## Instalar Git

### Windows
[Descargar Git para Windows](http://git-scm.com/download/win)

### Mac
Para verificar si está instalado Git, puedes abrir el terminal y ejecutar `git`, en caso que no esté instalado te saldrá un prompt para instalar los command line tools de Xcode o sino lo puedes descargar directamente desde [aquí](http://git-scm.com/download/mac)

### Linux
A través del package manager que use tu distribución de Linux:
- `sudo apt-get install git-all`
o sino
- `sudo yum install git-all`


## Customizar la línea de comando
La línea de comando en Mac y Linux se la puede personalizar para que muestre información adicional del repositorio a simple vista, toda línea de comando tiene su perfil en un archivo oculto en la carpeta home: `~/.bash_profile`

Dentro de la carpeta utils, adjunto tres archivos que deberán tener para hacer que su vida sea más fácil con la línea de comando
- `bash_profile`
- `git-prompt.sh`
- `git-completion.bash`

Los cuales deberán ser pegados en la ruta home como archivos ocultos, que quiere decir esto? que haremos algo como lo siguiente en el terminal:
- `cp /ruta/al/archivo/git-prompt.sh ~/.git-prompt.sh`
- `cp /ruta/al/archivo/git-completion.bash ~/.git-completion.bash`
- Revisar si ya existe el archivo `.bash_profile` si no existe seguir con el mismo paso que los otros `cp /ruta/al/archivo/bash_profile ~/.bash_profile`, caso contrario, solo es necesario copiar el contenido de `bash_profile` en el archivo ya existente de `.bash_profile`
- Decirle al terminal que tiene que actualizar su perfil con `source ~/.bash_profile`

## Configurar Git
Vamos a configurar el nombre, email y editor que va a usar git en la computadora
- `git config --global user.name "Mi nombre aquí"`
- `git config --global user.email "Mi mail aquí"`
- `git config --global core.editor "Ruta/al/ejecutable"`

## Generar llaves SSH
### Configurar computadora
Una vez ya creada la cuenta de Github:
- Para generar llaves, se debe ejecutar el siguiente comando: `ssh-keygen -t rsa -C "gacarlo89@gmail.com"`.
- Luego te pedirán la ruta con el nombre de donde lo quieres guardar, si lo dejas en vacío, generarás la llave con la ruta y nombre que están en paréntesis
- Es opcional que le pongas un password a tu key
- Luego de terminar de generar el key, se generan dos archivos, si lo dejaste en predeterminado, se llamarán `id_rsa` y `id_rsa.pub`
- Asegurate de que el agente de autenticación esté corriendo con los comandos:

> En windows
`eval $(ssh-agent)`
> Los demás
`eval "$(ssh-agent -s)"`

- Agregar el key en el agente con el comando: `ssh-add ~/.ssh/id_rsa`
### Configurar Github
- Abrir con tu editor favorito el archivo `id_rsa.pub` que generamos, o puedes abrirlo con vim: `vim id_rsa.pub`
- Ir a Account->Settings->SSH Keys en Github, agrega una nueva llave SSH y copia el contenido del archivo `id_rsa.pub`

Con eso ya deberías poder realizar commits a través de SSH

### Troubleshooting
En caso que no te permita hacer push, revisa con `git remote -v` para que veas si estás apuntando a los repositorios a través de HTTPS o de SSH