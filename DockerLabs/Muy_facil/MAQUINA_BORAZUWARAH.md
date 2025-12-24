## Resolución máquina BorazuwarahCTF

Comenzamos con un escaneo a la ip de la maquina victima

![image alt](https://github.com/Di3goAlvZ/LabsCS/blob/main/images/ss16.png?raw=true)

vemos que tiene el puerto 22 y el 80 abiertos, si nos fijamos en el puerto 80 tiene un servicio http corriendo

------------------------------------------------

ingresada la ip de la máquina en el navegador nos devuelve esto

![image at](https://github.com/Di3goAlvZ/LabsCS/blob/main/images/ss17.png?raw=true)

------------------------------------------------

En esta parte me guie de un write-up en el cual hacia uso de exiftool, una herramienta que tiene como función principal leer, escribir y editar los metadatos que estan escondidos dentro de casi cualquier archivo digital como imagenes, videos, etc

![image at](https://github.com/Di3goAlvZ/LabsCS/blob/main/images/ss18.png?raw=true)

una vez usada la herramienta vemos un dato clave que es el usuario llamado “borazuwarah”

------------------------------------------------

sabiendo el usuario procedemos a hacer fuerza bruta con hydra:

![image at](https://github.com/Di3goAlvZ/LabsCS/blob/main/images/ss19.png?raw=true)

y como podemos ver encontro el password que es 123456

-------------------------------------------------

Por lo que ahora entraremos a la máquina por medio de ssh

![image alt](https://github.com/Di3goAlvZ/LabsCS/blob/main/images/ss20.png?raw=true)

-------------------------------------------------

una vez dentro, es turno de la escalada de privilegios

![image alt](https://github.com/Di3goAlvZ/LabsCS/blob/main/images/ss21.png?raw=true)

nos devuelve que podemos ser usuario root con BASH, por lo que ahora buscaremos ese binario en GFTOBins

-------------------------------------------------

una vez hecha la busqueda usaremos:


![image alt](https://github.com/Di3goAlvZ/LabsCS/blob/main/images/ss22.png?raw=true)

entonces este sistema puede usar bash como administrador por lo que una vez usado el comando sudo bash los permisos de administrador se heredan a todo lo demás

----------------------------------------------------

y aqui comprobamos que ya somos usuarios root

![image alt](https://github.com/Di3goAlvZ/LabsCS/blob/main/images/ss23.png?raw=true)
