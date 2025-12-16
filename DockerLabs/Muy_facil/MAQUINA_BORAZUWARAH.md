# Resolución máquina BorazuwarahCTF

Comenzamos con un escaneo a la ip de la maquina victima

vemos que tiene el puerto 22 y el 80 abiertos, si no fijamos en el puerto 80 tiene un servicio http corriendo

ingresada la ip de la máquina en el navegador nos devuelve esto

En esta parte me guie de un write-up en el cual hacia uso de exiftool, una herramienta que tiene como función principal leer, escribir y editar los metadatos que estan escondidos dentro de casi cualquier archivo digital como imagenes, videos, etc

una vez usada la herramienta vemos un dato clave que es el usuario llamado “borazuwarah”

sabiendo el usuario procedemos a hacer fuerza bruta con hydra:

y como podemos ver encontro el password que es 123456

Por lo que ahora entraremos a la máquina por medio de ssh

una vez dentro, es turno de la escalada de privilegios

nos devuelve que podemos ser usuario root con BASH, por lo que ahora buscaremos ese binario en GFTOBins

una vez hecha la busqueda usaremos:

entonces este sistema puede usar bash como administrador por lo que una vez usado el comando sudo bash los permisos de administrador se heredan a todo lo demás

y aqui comprobamos que ya somos usuarios root
