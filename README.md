ZF2 Aplicacion Básica
=======================

Introdución
------------

Esta es una plantilla simple con la que pueden comenzar a crear
sus aplicaciones basadas en Zend Framework 2. También cuanta 
con Bootstrap 3 como base para crear la vista.

Incluye
-------
* Manejo de usuarios
* Login
* Administrador

### Modo desarrollo

    # Habilitar
    $ php ./public/index.php development enable
    
    # Deshabilitar
    $ php ./public/index.php development disable

### Instalación usando el archivo tar.gz

Si no tienes instalado Composer de forma global puedes hacer lo siguiente:

1. Descargar [Zf2AplicacionBasica](https://github.com/elialejandro/Zf2AplicacionBasica/tarball/master), 
   extraer y despues instalar las dependencias:

        cd mi/proycto/dir
        curl -#L https://github.com/elialejandro/Zf2AplicacionBasica/tarball/master | tar xz --strip-components=1
    

2. Descargar composer en el directorio del proyecto e instalar las dependencias:

        curl -s https://getcomposer.org/installer | php
        php composer.phar install

Configuración del servidor web
------------------------------

### PHP CLI server

Simplemente ejecutar el siguiente comando:

    php -S 0.0.0.0:8080 -t public/ public/index.php

Este servidor debería de iniciar en el puerto 8080, y estar configurado en todas las interfaces de red.

**Note:** El servidor CLI es *solo para desarrollo*.

### Servidor Vagrant

Este proyecto incluse una configuración básica de [Vagrant](http://docs.vagrantup.com/v2/getting-started/index.html)  que se ejecuta sobre [VirtualBox](https://www.virtualbox.org/wiki/Downloads).

1. Ejecutar el comando:

    vagrant up

2. Visitar [http://localhost:8085](http://localhost:8085) en tu navegador

Mira el archivo [Vagrantfile](Vagrantfile) para detalles de la configuración.

### Configuración de Apache

Si tienes un servidor instalado en tu ordenador puedes crear un host virtual con la siguiente configuración:

    <VirtualHost *:80>
        ServerName zf2-app.localhost
        DocumentRoot /path/to/zf2-app/public
        <Directory /path/to/zf2-app/public>
            DirectoryIndex index.php
            AllowOverride All
            Order allow,deny
            Allow from all
            <IfModule mod_authz_core.c>
            Require all granted
            </IfModule>
        </Directory>
    </VirtualHost>
