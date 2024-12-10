# Índice

- [Índice](#índice)
  - [Actualización del sistema](#actualización-del-sistema)
  - [Instalación de Git](#instalación-de-git)
  - [Instalación de Hugo](#instalación-de-hugo)
    - [Descargar el paquete de Hugo](#descargar-el-paquete-de-hugo)
    - [Instalación del paquete .deb](#instalación-del-paquete-deb)
  - [Comprobación de la versión de Hugo](#comprobación-de-la-versión-de-hugo)
  - [Creación de un nuevo sitio](#creación-de-un-nuevo-sitio)
  - [Creación de repositorio en GitHub](#creación-de-repositorio-en-github)
  - [Inicialización del repositorio Git](#inicialización-del-repositorio-git)
  - [Adición de un tema en Hugo](#adición-de-un-tema-en-hugo)
    - [Agregar el submódulo del tema](#agregar-el-submódulo-del-tema)
  - [Añadir el tema a la configuración](#añadir-el-tema-a-la-configuración)
  - [Creación de contenido en Hugo](#creación-de-contenido-en-hugo)
    - [Crear una página](#crear-una-página)
    - [Crear publicaciones o posts](#crear-publicaciones-o-posts)
    - [Crear un "leaf bundle"](#crear-un-leaf-bundle)
  - [Configuración de archivos](#configuración-de-archivos)
  - [Construcción del sitio](#construcción-del-sitio)
  - [Despliegue en el servidor local](#despliegue-en-el-servidor-local)
  - [Subir al GitHub](#subir-al-github)
  - [Despliegue en en Netlify](#despliegue-en-en-netlify)
    - [Conectamos a gitHub repo](#conectamos-a-github-repo)
    - [Configurar los parámetros de construcción](#configurar-los-parámetros-de-construcción)
    - [Desplegar el sitio](#desplegar-el-sitio)
  - [Despliegue en el GitHub pages](#despliegue-en-el-github-pages)


## Actualización del sistema
- Antes de comenzar la instalación, actualizamos los repositorios con el siguiente comando: **"sudo apt update -y"**
  
## Instalación de Git
- En caso de que no tenemos git anteriormente instalamos de nuevo con el comando: **"sudo apt install git"**
  
## Instalación de Hugo
### Descargar el paquete de Hugo
- Para instalar Hugo, primero descargamos el archivo .deb usando el comando wget.
- comando : **" wget https://github.com/gohugoio/hugo/releases/download/v0.135.0/hugo_extended_0.135.0_linux-amd64.deb"**
  
### Instalación del paquete .deb

- Una vez descargado el archivo, instalamos el paquete .deb con el siguiente comando: **"apt install ./hugo_extended_0.135.0_linux-amd64.deb"**

## Comprobación de la versión de Hugo
- Después de instalar Hugo, verificamos que la instalación se haya realizado correctamente ejecutando: **"hugo version"**
  

## Creación de un nuevo sitio

- creamos un nuevo sitio de Hugo utilizando el siguiente comando: **"hugo new actividad22_1_RRH"**
- Y cambiamos el directorio con el comando: **"cd actividad22_1_RRH"**
  
## Creación de repositorio en GitHub

- Creamos un nuevo repositorio sin README.md.
- Copiamos su enlace.
  
## Inicialización del repositorio Git

- Después de creaxión del sitio Hugo, inicializamos este repositorio Git y conéctamos a un repositorio remoto en GitHub. Los comandos para hacerlo son: **"git init"**
- **"git remote add origin https://github.com/tu_cuenta_github/myblog.git"**

## Adición de un tema en Hugo
### Agregar el submódulo del tema
- Hugo no viene con un tema preconfigurado, así que añadimos uno manualmente. 
- El siguiente muestramos cómo agregar el tema "Ananke": **"git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke"**
  
## Añadir el tema a la configuración
- Después de agregar el submódulo, editamos el archivo de configuración hugo.toml para incluir el tema: **"echo "theme = 'ananke'" >> hugo.toml"**

## Creación de contenido en Hugo
### Crear una página

- Para crear una página en Hugo, usa el siguiente comando: **"hugo new miembros.md"**
- Aquí Ponemos información sobre miembros de nuestro grupo.

### Crear publicaciones o posts
- Para crear publicaciones (posts) en Hugo, ejecutamos los siguientes comandos: **"hugo new posts/cala.md"** y
**"hugo new posts/rosa.md"**.
- Luego agregamo contenido de estos posts.

### Crear un "leaf bundle"
- Un "leaf bundle" es un directorio que incluye un archivo index.md y uno o más recursos. 
- Para crear un "leaf bundle", utilizamos el siguiente comando: **"hugo new about/index.md"**.

## Configuración de archivos

- Hugo soporta tres formatos de configuración: YAML, JSON y TOML. Por defecto, Hugo utiliza el formato TOML.
- Aquí Configuramos el archivo hugo.toml donde ponemos baseurl, languageCodetitle, theme.
- También ponemos menu para nuestro sitio.
  

## Construcción del sitio
- Para generar el sitio estático (HTML, CSS, JS), utilizamos el siguiente comando: **"hugo"**
- El sitio se almacenará en un directorio llamado public. A continuación, puedes copiar este directorio al servidor web utilizando comandos como FTP, SSH o SCP.

- También puedemos arrastrar la carpeta public a servicios de hosting en línea como Netlify o Cloudflare.

- Para GitHub Pages, solo podrás asociar la carpeta docs con el siguiente comando: **"hugo -d docs"**
- 



## Despliegue en el servidor local

- Para ver el sitio en tu servidor de desarrollo local, ejecuta el siguiente comando: **"hugo server"**
- Esto lanzará un servidor local donde podrás ver los cambios realizados en tu sitio.

## Subir al GitHub
- Para subir al github utilizamos los comandos de Git habituales:
- **git add .**
- **git commit -m "Configuración del sitio Hugo"**
- **git push origin master**

## Despliegue en en Netlify

- Netlify es una plataforma popular para desplegar sitios web estáticos. A continuación se describen los pasos para desplegar tu sitio Hugo en Netlify.
### Conectamos a gitHub repo
- Estos son los pasos para conectar a repositorio de GitHub:

1. En el panel de control de Netlify, hacemos clic en "New site from Git".
2. Seleccionamos GitHub como fuente de tu repositorio.
3. Autorizamos a Netlify para acceder a mi cuenta de GitHub, si aún no lo has hecho.
4. Eligimos el repositorio de actividad22_1_RRH

### Configurar los parámetros de construcción

Después de seleccionar el repositorio, Netlify nos ìde configurar los parámetros de construcción. 

- **Branch to deploy**: Seleccionamos la rama `master`
- **Build command**: Escribimos `hugo` para generar el sitio estático.
- **Publish directory**: Especificamos el directorio `public`, que es donde Hugo genera los archivos estáticos.

###  Desplegar el sitio

Hacmos clic en "Deploy site" y Netlify comenzará a construir y desplegar tu sitio. El proceso puede tardar unos minutos.

## Despliegue en el GitHub pages
- para desplegar al github pages eliminamos carpeta **public** y creamos docs.
- También creamos carpetas y fichero de hugo.yml **".github/workflows/hugo.yml"**
- Añadimos el contenido en el fichero.
- En gitHub pages seleccionamos **"GitHub Actions"**.
  
