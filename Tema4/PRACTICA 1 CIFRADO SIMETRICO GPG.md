## 1. Crea un documento de texto con cualquier editor o utiliza uno del que dispongas. 
## 2. Cifra este documento con alguna contraseña acordada con el compañero de al lado. 
## 3. Haz llegar por algún medio al compañero de al lado el documento que acabas de cifrar. 
## 4. Descifra el documento que te ha hecho llegar tu compañero de al lado. 
Creo el documento 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/1.PNG)

Lo cifro con GPG

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/2.PNG)

Nos crea el documento.txt.gpg que esta cifrado

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/3.PNG)

Ahora lo desciframos 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/4.PNG)

## 5. ¿Con qué algoritmo se ha cifrado el fichero? Vuelve a cifrar el fichero usando el algoritmo AES256. ¿Puedes hacer permanente esta configuración? 
Para saber el cifrado usamos  **gpg --list-packets documento.txt.gpg**

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/5.PNG)

Ya estamos usando AES256, en caso de querer usar otro algoritmo lo indicariamos en el comando :
**gpg -c --cipher-algo BLOWFISH documento.txt** , y si queremos que sea permanente, (creamos el fichero si no existe) en /home/kali/.gnupg/gpg.conf añadimos **cipher-algo BLOWFISH**

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/6.PNG)

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/7.PNG)

## 6. Instala gpg en windows (Gpg4win), repite el ejercicio en Windows. Puedes encriptar un mensaje en linux y desencriptarlo en windows y al contrario. 
Para windows debemos descargarlo de su sitio official https://gnupg.org/ e instalarlo.
Ahora con el archivo cifrado de kali que hemos traido a windows vamos a desencriptarlo, para eso usamos la aplicacion grafica,

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/11.PNG)

Y nos devuelve el documento descifrado

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/12.PNG)

## 7. openssl es otra herramienta que nos permite cifrar mensajes de forma simétrica, investiga como se realiza este ejercicio utilizando esta herramienta. 
Para usar openssl para encriptar el mismo archivo usamos el siguiente comando:
**openssl enc -aes-256-cbc -salt -in documento.txt -out documento_encrypted.txt**

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/8.PNG)

Y para descifrar:
**openssl enc -d -aes-256-cbc -in documento_encrypted.txt -out documento_decrypted.txt**

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/9.PNG)

Aqui vemos los documentos el encriptado y el desencriptado respectivamente

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/1/10.PNG)

