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
------------------------------------ 
En primer lugar instalamos la distribución debian:
<pre>
sudo debootstrap --arch=amd64 wheezy debian http://ftp.debian.org/debian/
</pre>
Accedemos a la distribucion con chroot de la siguiente manera:
<pre>
chroot Documentos/4/debian
</pre>

Objetivo 2 "Instalación de modulos necesarios"
----------------------------------------------
Lo primero que debemos de hacer es asegurarnos de que tenemos los repositorios actualizados para esto usamos apt-get update.
Para nuestra practica necesitaremos como ya he comentado antes apache y mysql. Instalemoslos:
<pre>
apt-get install apache2
apt-get install mysql-server
aptitude install php5 libapache2-mod-php5
apt-get install phpmyadmin
</pre>
Durante la instalación de mysql nos solicitará una contraseña de acesso, la cual no puede ser vacia por motivos de seguridad.
Si accedemos a la dirección localhost desde un navegador nos aparecerá el index por defecto de apache 'Its work!' con lo cual nos indica que esta bien instalado.
Hemos instalado tambien phpmyadmin para que nos resulte más sencillo el manejo de base de datos que desde el terminal. 
Durante la instalación nos realiza varias preguntas como por ejemplo que servidor web tenemos instalado y la contraseña para acceder a las bases de datos. 
El programa de instalación crea un enlace simbólico en el DocumentRoot del servidor web para que la aplicación pueda ser accesible desde la url: http://ip-del-servidor-web/phpmyadmin/index.php. Si no se viera la aplicación en dicha url, quizás sea por algún aspecto de la configuración de apache. 
En tal caso, lo más sencillo sería mover la carpeta de phpmyadmin directamente dentro del DocumentRoot del servidor y asignar al usuario www-data que es el usuario con el que se ejecuta el apache, para que apache pueda acceder a dicha carpeta:
<pre>
mv /usr/share/phpmyadmin /var/www/ (en nuestro caso)
chown -R www-data /var/www/phpmyadmin.
</pre>
Volvemos a probar y nos devuelve el siguiente error:
![captura 1] (https://dl.dropbox.com/s/jz8wfhq0sqi8j2m/error_phpmyadmin.png)

Para resolver esto instalaremos los siguientes paquetes:
<pre>
apt-get install php5-mysql php5-curl php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
</pre>
Continua dando el error, pararemos los servicios y los arrancaremos de nuevo; reiniciamos el sistema y arrancamos los dos servicios:
<pre>
etc/init.d apache2 start
etc/init.d mysql start
</pre>
Si volvemos a intentarlo ya estará listo para acceder.

![captura 2] (https://dl.dropbox.com/s/vddgcw5ndnjws0d/mysqlfuncionando.png)


Objetivo 3 "Importar mi programa"
---------------------------------


Prueba de funcionamiento
------------------------
