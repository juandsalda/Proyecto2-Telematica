# Despligue en un Servidor Linux2 en AWS
Fuente: https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/ec2-lamp-amazon-linux-2.html

Para realizar el despliegue de WordPress en AWS se deben realizar el procedimiento descrito a continuación:
*Para la realización de este procedimiento se asume que se tiene una instancia EC2 en AWS ejecutandose, y que se puede conectar a esta. En caso de no cumplir estos prerequisitos revisar el siguiente tutorial: https://docs.aws.amazon.com/es_es/AWSEC2/latest/UserGuide/EC2_GetStarted.html#ec2-launch-instance

## Se instala un servidor LAMP

### 1. Conectarse a la instancia

### 2. Se actualizan todos los paquetes de software

[ec2-user ~]$ sudo yum update -y
