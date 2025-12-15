Resolución de la máquina TRUST de DockerLabs\
\
Comenzamos haciendo un escaneo con nmap\
Podemos ver que tiene el puerto 80 abierto, en el cual está corriendo un
servidor apache, al igual que tiene abierto el servicio ssh

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss1.png?raw=true)

Ingresamos la ip de la maquina victima y nos devuelve esto:

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss2.png?raw=true)

Usamos la herramienta gobuster para encontrar directorios o archivos
ocultos en el servidor web que en este caso es el apache

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss3.png?raw=true)

Como podemos ver gobuster devolvió un archivo html y un php asi como un
server status, por curiosidad revise el .html copiandolo junto con la
url en el navegador, el cual no tuvo respuesta y luego pase al .php el
cual sí me respondió con este mensaje

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss4.png?raw=true)

La web pertenece a alguien llamado Mario por lo que es una pista para el
siguiente paso

En el escaneo aparte del puerto 80 mostró el 22, un servicio ssh, como
también tenemos la pista que el usuario de la web es alguien llamado
Mario procedemos a hacer un ataque de fuerza bruta con Hydra, ya que al
estar un servicio ssh y al tener un nombre de usuario lo que buscaremos
sera la contraseña de dicho usuario para tener acceso

Recordemos que Hydra es una herramienta que automatiza ataques de fuerza
bruta contra servicios de autenticación como ssh, ftp, http, probando
miles de combinaciones de usuario o contraseña hasta encontrar las
credenciales correctas

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss5.png?raw=true)

le indicamos a hydra que queremos la contraseña del usuario mario y
efectivamente pudo encontrarla que en este caso es "chocolate"

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss6.png?raw=true)

pudimos entrar

ahora verificamos si tenemos el permiso de superusuario utilizando sudo
-l

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss7.png?raw=true)

nos devuelve que tenemos que usar vim como usuario root, así que ahora
pasamos a explotar esto

recurri a GFTOBins, esta plataforma nos muestra cómo explotar este tipo
de programa para obtener una shell root o realizar acciones
privilegiadas.

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss8.png?raw=true)

obtenido esto ejecutamos el siguiente comando:

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss9.png?raw=true)

lo cual nos devolverá que somos usuario root

![image alt](https://github.com/Cyberdieg0/LabsCS/blob/main/images/ss10.png?raw=true)

Listo, máquina resuelta.
