# Práctica: Cifrado asimétrico con gpg y openssl 
## Cifrado asimétrico con gpg
En esta práctica vamos a cifrar ficheros utilizando cifrado asimétrico utilizando el programa gpg. Puedes encontrar el resumen de comando en esta chuleta o buscar información en internet. 

## Tarea 1: Generación de claves (1 punto) 
Los algoritmos de cifrado asimétrico utilizan dos claves para el cifrado y descifrado de mensajes. Cada persona involucrada (receptor y emisor) debe disponer, por tanto, de una pareja de claves pública y privada. Para generar nuestra pareja de claves con gpg utilizamos la opción --gen-key: 

Para esta práctica no es necesario que indiquemos frase de paso en la generación de las claves (al menos para la clave pública) 

### 1. Genera un par de claves (pública y privada). ¿En que directorio se guarda las claves de un usuario? 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/1.PNG)

Esta se guarda en el directorio /home/kali/.gnupg/

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/2.PNG)

### 2. Lista las claves públicas que tienes en tu almacén de claves. Explica los distintos datos que nos muestra. ¿Cómo deberías haber generado las claves para indicar, por ejemplo, que tenga un 1 mes de validez? 
Podemos listar las claves publicas con 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/3.PNG)

Para cambiar la clave y que tenga un mes de validez

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/5.PNG)

y en el editor ponemos expire y la cantidad de tiempo 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/6.PNG)

### 3. Lista las claves privadas de tu almacén de claves. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/4.PNG)


## Tarea 2: Importar / exportar clave pública (1 punto) 
Para enviar archivos cifrados a otras personas, necesitamos disponer de sus claves públicas. De la misma manera, si queremos que cierta persona pueda enviarnos datos cifrados, ésta necesita conocer nuestra clave pública. Para ello, podemos hacérsela llegar por email por ejemplo. Cuando recibamos una clave pública de otra persona, ésta deberemos incluirla en nuestro keyring o anillo de claves, que es el lugar donde se almacenan todas las claves públicas de las que disponemos. 
### 1. Exporta tu clave pública en formato ASCII y guardalo en un archivo nombre_apellido.asc y envíalo al compañero con el que vas a hacer esta práctica. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/7.PNG)

### 2. Importa las claves públicas recibidas de vuestro compañero. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/8.PNG)

### 3. Comprueba que las claves se han incluido correctamente en vuestro keyring. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/9.PNG)

## Tarea 3: Cifrado asimétrico con claves públicas (3 puntos) 
Tras realizar el ejercicio anterior, podemos enviar ya documentos cifrados utilizando la clave pública de los destinatarios del mensaje. 
### 1. Cifraremos un archivo cualquiera y lo remitiremos por email a uno de nuestros compañeros que nos proporcionó su clave pública. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/10.PNG)

### 2. Nuestro compañero, a su vez, nos remitirá un archivo cifrado para que nosotros lo descifremos. 
### 3. Tanto nosotros como nuestro compañero comprobaremos que hemos podido descifrar los mensajes recibidos respectivamente. 
Ahora para desencriptar el de ubuntu es el siguiente comando, se asume que ya se tiene la clave importada

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/10-5.PNG)

### 4. Por último, enviaremos el documento cifrado a alguien que no estaba en la lista de destinatarios y comprobaremos que este usuario no podrá descifrar este archivo. 
### 5. Para terminar, indica los comandos necesarios para borrar las claves públicas y privadas que posees. 
Hay que tener en cuentar que para borrar las claves primero se ha de borrar la privada y despues la publica con gpg --delete-secret-key nombre_claves  borramos la privada y gpg --delete-key nombre_claves la publica

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/11.PNG)

## Tarea 4: Exportar clave a un servidor público de claves PGP (2 puntos) 

Para distribuir las claves públicas es mucho más habitual utilizar un servidor específico para distribuirlas, que permite a los clientes añadir las claves públicas a sus anillos de forma mucho más sencilla. 
### 1. Genera la clave de revocación de tu clave pública para utilizarla en caso de que haya problemas. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/12.PNG)

### 2. Exporta tu clave pública al servidor pgp.rediris.es 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/12-5.PNG)

### 3. Borra la clave pública de alguno de tus compañeros de clase e impórtala ahora del servidor público de rediris 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/13.PNG)

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/13-5.PNG)

## Tarea 5: Cifrado asimétrico con openssl (3 puntos) 

En esta ocasión vamos a cifrar nuestros ficheros de forma asimétrica utilizando la herramienta openssl. 
### 1. Genera un par de claves (pública y privada). 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/14.PNG)

### 2. Envía tu clave pública a un compañero. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/15.PNG)

### 3. Utilizando la clave pública cifra un fichero de texto y envíalo a tu compañero. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/16.PNG)

 - enc -aes-256-cbc: Tipo de cifrado simétrico. 
 - pass file:key.txt: La clave con la que cifrar el archivo. 
 - in: Fichero de entrada. 
 - out: Fichero de salida. 
 - rsautl: Indica que vamos a usar RSA para firmar, verificar, cifrar o descifrar. 
 - pkeyutl: Este comando de OpenSSL se utiliza para realizar operaciones de cifrado y descifrado con RSA.
 - inkey: Llave con la que cifrar -pubin: Indica que vamos a firmar con una llave pública.
   
### 4. Tu compañero te ha mandado un fichero cifrado, muestra el proceso para el descifrado. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/4/17.PNG)

