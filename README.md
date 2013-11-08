Practica2
=========

Objetivos
---------
1. Instalar un sistema debian en una carpeta local
2. Instalación de todos los modulos necesarios para correr mi programa
3. Importar mi programa

Descripción de mi programa
--------------------------
Trata de una plataforma web basada en un periodico, donde existen usuarios que pueden crear comentarios, existen administradores que pueden crear noticias, editarlas o borrarlas.
Para conseguir esto necesitaremos un servidor web `Apache` y un servidor `mysql` donde estarán todas tablas con los usuarios, noticias y comentarios.

Objetivo 1 "Instalar sistema debian"
---------- 
En primer lugar instalamos la distribución debian:
<pre>
sudo debootstrap --arch=amd64 wheezy debian http://ftp.debian.org/debian/
</pre>
Accedemos a la distribucion con chroot de la siguiente manera:
<pre>
chroot Documentos/4/debian
</pre>


Objetivo 2 "Instalación de modulos necesarios"
----------
Lo primero que debemos de hacer es asegurarnos de que tenemos los repositorios actualizados para esto usamos apt-get update.


Objetivo 3 "Importar mi programa"
----------


Prueba de funcionamiento
------------------------
