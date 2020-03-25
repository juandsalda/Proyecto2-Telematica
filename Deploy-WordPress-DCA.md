# Despligue en un Servidor Centos 7.x en el DCA

Fuentes:
https://fututel.com/es/tutoriales-guias-manuales-videotutoriales/2590-iniciar-sesion-en-un-servidor-con-putty-usuarios-de-windows
https://cerebro-digital.com/panel/knowledgebase/63/Comandos-frecuentes-de-Docker.html
https://docs.docker.com/install/linux/docker-ce/centos/
https://www.linode.com/docs/quick-answers/linux/wordpress-with-docker-compose/ 

Para realizar el despliegue de WordPress en el DCA se debe realizar el procedimiento descrito a continuación:

1. Se descarga Putty en el siguiente link: **
https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
2. se descarga OpenVPN en el siguiente link: **
https://openvpn.net/community-downloads/
3. Ingresamos a OpenVPN ingresando El Usuario y la contraseña.
4. Ingresamos a Putty:
Ingresamos el campo de Ip Addres, Vamos a connection>SSH>Auth>tunnels
Configuramos el tunel por el puerto 8080 y click en el boton add.
Hacemos click en Open y nos habre un cmd, en el CMD ingresamos USER & PASSWORD.

5. una vez se establece la conexión con el DCA ingresamos los comandos:
5.1
$ sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine

con estos comando removemos versiones antiguas de Docker.

5.2
$ sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2

Con estos comandos instalamos los paquetes requeridos

5.3
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
con estos comandos instalamos Docker

5.4
$ sudo systemctl start docker

con este comando iniciamos Docker

5.5
$ sudo docker run hello-world

con este comando verificamos que Docker este corriendo correctamente con su contendor por defecto

5.6

$ sudo yum install /path/to/package.rpm

con este comando instala Docker Engine - Community, cambiando la ruta a continuación a la ruta donde descargó el paquete Docker.

5.7
$sudo systemctl start docker

con este comando inicia docker

5.8
$ sudo docker run hello-world
 
Con este comando verificamos que la imagen corra correctamente

6. Creamos un fichero llamado con el comando
$mkdir Proyectos2
$mkdir grupo26

7. Creamos el archivo de texto 
$touch docker-compose.yml

8. Accedemos al archivo de texto para editarlo.
$vi docker-compose.yml

9. despues de acceder ingresamos la especificacion tecnica como servicios que usaremos y que tipos de bases de Datos
_________________________________________________________

     
    version:'3.3'
    services:

    wordpress:
   
     depends_on:
     
       - db
       
     image: wordpress:latest
     
     volumes:
     
       - wordpress_files:/var/www/html
       
     ports:
     
       - "80:80"
       
     restart: always
     
     environment:
     
       WORDPRESS_DB_HOST: db:3306
       
       WORDPRESS_DB_USER: wordpress
       
       WORDPRESS_DB_PASSWORD: my_wordpress_db_password
       

    db:
   
     image: mysql:5.7
     
     volumes:
     
       - db_data:/var/lib/mysql
       
     restart: always
     
     environment:
     
       MYSQL_ROOT_PASSWORD: my_db_root_password
       
       MYSQL_DATABASE: wordpress
       
       MYSQL_USER: wordpress
       
       MYSQL_PASSWORD: my_wordpress_db_password
       
    volumes:

    wordpress_files:
    
    db_data:

________________________________________________________

10. Guardamos el documento oprimiendo CTRL + C, este comando nos manda al pie del documento donde agregamos ":wq" para guardar y salir.

11. Una vez en la terminar lanzamos la imagen del Docker
$docker-compose up -d

12. una vez lanzada la imagen abrimos nuestro navegador preferido e ingresamos
localhost/

13. allí configuramos el docker y la pagina esta desplegada en el servidor local
Ingresamos el nombre de sitio, Usuario y contraseña.


14. Despues de estos nos encontramos en el Dashboard de la pagina y administrador del wordpress, podemos modificar directamente apariencia.

15. hacemos click en el boton ver pagina, este desarrollo es realizado con Docker en el DCA de la Universidad EAFIT y desplegada en el mismo.
  
  
