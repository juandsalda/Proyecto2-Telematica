# Despligue en un Servidor Linux2 en AWS
Fuente: https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/ec2-lamp-amazon-linux-2.html

Para realizar el despliegue de WordPress en AWS se deben realizar el procedimiento descrito a continuación:
*Para la realización de este procedimiento se asume que se tiene una instancia EC2 en AWS ejecutandose, y que se puede conectar a esta. En caso de no cumplir estos prerequisitos revisar el siguiente tutorial: https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/EC2_GetStarted.html#ec2-launch-instance

## Se instala un servidor LAMP

### 1. Conectarse a la instancia

### 2. Se actualizan todos los paquetes de software

  [ec2-user ~]$ sudo yum update -y

### 3. Se instalan los repositorios lamp-mariadb10.2-php7.2 y php7.2

  [ec2-user ~]$ sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2

### 4. Se instalan los paquetes de software PHP, MariaDB y el servidor web Apache

  [ec2-user ~]$ sudo yum install -y httpd mariadb-server 
  
### 5. Iniciamos el servidor Apache
  
  [ec2-user ~]$ sudo systemctl start httpd
  
## Se establecen los permisos de archivo

### 1. Añadir el usuario (ec2-user) al grupo apache

  [ec2-user ~]$ sudo usermod -a -G apache ec2-user
  
### 2. Cierre sesión 

  [ec2-user ~]$ exit
  
### 3. Cambie la propiedad de grupo de /var/www y su contenido al grupo apache

  [ec2-user ~]$ sudo chown -R ec2-user:apache /var/www
  
### 4. cambie los permisos del directorio /var/www y sus subdirectorios.
  
  [ec2-user ~]$ sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
  [ec2-user ~]$ find /var/www -type f -exec sudo chmod 0664 {} \;
  
## Proteger el servidor de base de datos
### 1. Inicie el servidor MariaDB.

 [ec2-user ~]$ sudo systemctl start mariadb

### 2. Ejecute mysql_secure_installation.

  [ec2-user ~]$ sudo mysql_secure_installation

  - Cambie la contraseña
  - Escriba Y para todas las opciónes
  
## Instalación de WordPress

### 1. Descargue el paquete de instalación de WordPress

  [ec2-user ~]$ wget https://wordpress.org/latest.tar.gz
  
### 2. Descomprima el archivo

  [ec2-user ~]$ tar -xzf latest.tar.gz

## Crear un usuario y base de datos para la instalación de WordPress

### 1. Inicie el servidor de base de datos

  [ec2-user ~]$ sudo systemctl start mariadb
  
### 2. Inicie sesión en el servidor de base de datos como el usuario root

  [ec2-user ~]$ mysql -u root -p
  
### 3. Cree un usuario y una contraseña para la base de datos MySQL

  CREATE USER 'wordpress-user'@'localhost' IDENTIFIED BY 'your_strong_password';
  
 *Del comando anterior asegurese de cambiar el nombre de usuario y la contraseña
  
### 4. Cree la base de datos

  CREATE DATABASE `wordpress-db`;
  
### 5. Conceder privilegios

  GRANT ALL PRIVILEGES ON `wordpress-db`.* TO "wordpress-user"@"localhost";
  FLUSH PRIVILEGES;
  exit

## Crear y modificar el archivo wp-config.php

### 1. Copie el archivo wp-config-sample.php en un archivo llamado wp-config.php. 
  
  [ec2-user ~]$ cp wordpress/wp-config-sample.php wordpress/wp-config.php

### 2. Modifique el archivo wp-config.php

  [ec2-user ~]$ nano wordpress/wp-config.php
  
### 3. Modifique los siguientes valores de acuerdo a lo configurado

  define('DB_NAME', 'wordpress-db');
  define('DB_USER', 'wordpress-user');
  define('DB_PASSWORD', 'your_strong_password');
 
### 4. Complete los siguientes valores. Para esto visite el siguiente enlace: https://api.wordpress.org/secret-key/1.1/salt/

  define('AUTH_KEY', '');
  define('SECURE_AUTH_KEY', '');
  define('LOGGED_IN_KEY',  '');
  define('NONCE_KEY', '');
  define('AUTH_SALT', '');
  define('SECURE_AUTH_SALT', '');
  define('LOGGED_IN_SALT', '');
  define('NONCE_SALT',  '');
  
### 5. Abra el archivo httpd.conf

  [ec2-user ~]$ sudo vim /etc/httpd/conf/httpd.conf
  
  #### Busque la sección que comienza por <Directory "/var/www/html">.
    Cambie la línea AllowOverride None por AllowOverride All

### 6. Instalar la biblioteca de dibujo de PHP

  [ec2-user ~]$ sudo yum install php72-gd

