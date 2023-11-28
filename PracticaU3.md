# Tema3

## 1
**libpam-cracklib**: se utiliza para mejorar la seguridad de las contraseñas en un sistema. Cuando está instalado, se integra con el sistema de autenticación PAM y permite configurar reglas y restricciones para la creación y modificación de contraseñas de usuarios. 

**rainbowcrack**:es una herramienta de cracking de contraseñas que utiliza tablas arcoíris precalculadas para acelerar el proceso de descifrado. Sirve para recuperar contraseñas mediante la comparación de hash almacenados con tablas arcoíris, reduciendo el tiempo necesario para descifrar contraseñas hash. Es especialmente eficiente en ataques contra hashes de contraseñas débiles y comúnmente utilizadas. Sin embargo, su efectividad disminuye ante el uso de salting y contraseñas complejas. 

**Pwdump**: es una herramienta utilizada para extraer y mostrar contraseñas en formato hash almacenadas localmente en un sistema Windows. Facilita el acceso a los hashes de contraseñas almacenados en el sistema para su posterior análisis o ataque, proporcionando información útil en auditorías de seguridad. Sin embargo, su uso ético es esencial, ya que puede violar la privacidad y los términos de servicio 

**L0phtCrack**: L0phtCrack es una herramienta de auditoría de contraseñas que realiza análisis de fuerza bruta y diccionario para evaluar la fortaleza de las contraseñas en un sistema, detectando vulnerabilidades de seguridad.

**NTPWEdit**: NTPWEdit es una utilidad que permite editar las contraseñas de usuarios en sistemas Windows al modificar el Registro del sistema, útil en casos de pérdida de contraseña o acceso a cuentas.

**John the Ripper**: John the Ripper es un programa de prueba de contraseñas que utiliza métodos de fuerza bruta y ataques de diccionario para descifrar contraseñas, siendo una herramienta versátil en auditorías de seguridad.

**Shadow Defender**: Shadow Defender crea un entorno virtual aislado en el sistema, permitiendo probar software o navegar por internet de forma segura sin afectar el sistema real, ya que cualquier cambio se revierte al reiniciar.

**Ofris**: Ofris es una herramienta de seguridad que ayuda a proteger sistemas Linux bloqueando la escritura en directorios importantes, previniendo la modificación no autorizada de archivos cruciales del sistema.

**Grub2**: Grub2 es un gestor de arranque utilizado en sistemas basados en Unix. Puede ser configurado para arrancar varios sistemas operativos y es esencial para el inicio del sistema en sistemas Linux y otros sistemas operativos compatibles con Unix.



## 2
Para ubuntu server instalamos sudo apt install libpam-cracklib y copiamos el archivo a root

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/2/1.PNG)

Editamos sudo nano /etc/pam.d/common-passwor, en el buscamos algo parecido a la siguiente linea:
password requisite pam_cracklib.so retry=3 minlen=8 difok=3

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/2/2.PNG)

Aqui es donde lo editaremos 
    - retry: número de intentos antes de que el sistema devuelva un error en la autenticación y nos expulse.
    
    - minlen: es la longitud mínima de la contraseña, por defecto está en 8 caracteres.
    
    - difok: número de caracteres diferentes que debe tener la nueva clave en comparación con la antigua.
    
    - ucredit: caracteres en mayúscula que debe tener como mínimo o máximo.
    
    - lcredit: caracteres en minúscula que debe tener como mínimo o máximo.
    
    - dcredit: el número de dígitos que debe tener como mínimo o máximo.
    
    - ocredit: el número de otros caracteres (símbolos) que debe tener la clave como mínimo o máximo.
    
Las opciones ucredit, lcredit,dcredit y ocredit pueden tener números negativos o positivos, para definir si queremos que tenga un rango de mínimo o máximo, por ejemplo:

    - lcredit=-2 : significa que como mínimo debe tener 2 caracteres en minúscula.
    
    - lcredit=+2 : significa que como máximo debe tener 2 caracteres en minúscula.
    

Yo solo voy a agregar que tenga una mayuscula para hacer la prueba con ucredit=-1, si pruebo no me dejara cambiar la contraseña hasta que meta una mayuscula 
![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/2/3.PNG)

Ahora en windows server

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/2/4.PNG)



En widows estamos mas limitados, si queremos que las contraseñas tengan mayus,signos y demas debemos tener habilitado los requisitos de complegidad, y en lo que mas podemos cambiar es el tamaño de esta y su duracion

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/2/5.PNG)

## 3
Generamos la tabla rainbow, con el siguiente comando 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/3/1.PNG)

    - rtgen: Invoca la herramienta RainbowCrack para generar tablas arcoíris.
    
    - ntlm: Especifica el algoritmo de hash, en este caso, NTLM.
    
    - loweralpha-numeric: Define el conjunto de caracteres que se utilizará para generar contraseñas, en este caso, letras minúsculas y dígitos.
    
    - 1: Longitud mínima de contraseña.
    
    - 5: Longitud máxima de contraseña.
    
    - 0: Desplazamiento de reducción, que en este caso es 0.
    
    - 2400: Número de cadenas reducidas generadas por cada cadena original.
    
    - 100000: Número total de cadenas originales generadas.
    
    - 0: Semilla aleatoria inicial para generar cadenas originales.
    
Ahora hay que ordenar la tabla para poder descifrar el hash (da igual desde que carpeta se lance rtgen la tabla se guarda en esta ruta)

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/3/2.PNG)

Ahora podemos descifrar el has de una de las contraseña del SAM, el has es la parte en amarillo 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/3/3.PNG)

Lo hacemos con el siguiente comando 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/3/4.PNG)

Como podemos ver abajo sale la contraseña despues del hash
**Si fueran contraseñas mas largas de 5 carateres, que tengan mayuculas o simbolos no funcionaria poque la tabla que he generado es para max 5 caracteres y minusculas y numeros, cuanto mas compleja la tabla mas tarda en generarse**


## 4
### 1
Para utilizar pwdump necesitamos descargarlo y para ello es necesario desactivar windows defender porque te bloquea el paquete por seguridad
Una vez echo abrimos un cmd como admin y nos vamos a la ruta donde este el pwdump8.exe (en mi caso uso la version 8) y lo ejecutamos mandando la salida a un archivo 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/1.PNG)

Y si vemos el archivo aparecen los usuarios con los hashs

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/2.PNG)

### 2
Comporbamos que sploits podemos usar para entrar a windwos con el siguiente comando

msf6 > sudo nmap -Pn -sS -p135,139,445,31337 -sV -O --osscan-guess --script vuln 192.168.1.34

Podemos ver como smb-vuln-ms17-010 es vulnerable

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/2-1.PNG)

Procedemos a usar y configurar el sploit

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/2-2.PNG)

Una vez dentro ejecutamos hashdump para optener el sam 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/2-3.PNG)

Ahora vamos a craquearlas con L0phtCrack , el proceso es "sencillo" instalamos el programa, le pasamos el archivo y seleccionamos como de "duras" son las contraseñas  a mas, mas tiempo tardara, yo he seleccionado la rapida y solo ha averiguado la de vagrant

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/2-4.PNG)


## 3
Para cambiar la contraseña con una herramienta LIVE yo utilizare Hiren's BootCD PE.
Una vez dentro del SO del Hiren vamos a la siguiente aplicación

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/3-1.PNG)

En el programa ponesmo la ruta del sam y lo abrimos, yo voy a cambiar la contraseña del usuario vagran a 12345

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/3-2.PNG)

Y he podido inicar en el usuario vagrant con la clave 12345

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/4/3-3.PNG)


## 5
Para descifrar contraseñas en linux usando john the ripper, primero creo un fichero uniendo shadows y passwd

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/5/1.PNG)

    - unshadow: Es un comando proporcionado por John the Ripper que combina las entradas de /etc/passwd y /etc/shadow.
    
    - /etc/passwd y /etc/shadow: Son archivos que contienen información sobre usuarios y contraseñas en sistemas Linux. 
    

Ahora iniciamos john diciendole el formato de las contraseñas crypt que es para sistemas linux,

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/5/2.PNG)

Auque antes veiamos que ha descifrado una es porque es de un usuario nuevo que he creado para esta prueba, con el siguiente comando podemos ver las contraseñas descifradas

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/5/3.PNG)

## 6
Para congelar Windows voy a usar Shadow Defender, para ello lo instalo que basicamente es siguiente, siguiente . Al completar abrimos el programa seleccionamos el disco a congelar y le damos a Shadow Mode y nos saldra tal q asi 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/6/1.PNG)

Ahora creo una carpeta y un archivo para hacer la prueba 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/6/2.PNG)


Y despues de reiniciar 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/6/3.PNG)

Para "descongelarlo" seleccionamos el disco y Exit Shadow mode

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/6/4.PNG)

Ahora en linux usare Ofris para instalarlo uso el siguiente comando:

if [ $(uname -m) == "x86_64" ]; then deb="http://goo.gl/DleLl"; else deb="http://goo.gl/V94Qs"; fi && wget -q $deb -O ofris.deb && sudo dpkg -i ofris.deb && rm ofris.deb

Lo iniciamos con ofris-en que nos da este menu donde seleccionaremos el 3

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/6/5.PNG)

Una vez seleccionano no hay que hacer nada, creamos unos ficheros de prueba

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/6/6.PNG)

Reiniciamos y podemos comprobar que no estan 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/6/7.PNG)

## 7
Para configurar una contraseña para el grup instalamos grub2 y despues generamos una contraseña con el siguiente comando 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/7/1.PNG)

despues abrimos /etc/default/grub y añadimos el hash y el usuario a la siguiente linea

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/7/2.PNG)

Guardamos y actualizamos con  sudo update-grub, ahora para darle contraseña vamos al archivo sudo nano /etc/grub.d/40_custom y agregamos el usuario y el hash

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/7/3.PNG)

Despues hacemos sudo update-grub y reiniciamos, como podemos ver nos pide el usuario y la contraseña que hemos puesto en  /etc/grub.d/40_custom, si fallamos nos lleva a la pantalla del gurb que da igual en la opcion que nos metamos nos pedira usuario y contraseña

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/7/4.PNG)

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/7/5.PNG)

Si lo metemos bien nos deja pasar 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema3/7/6.PNG)
