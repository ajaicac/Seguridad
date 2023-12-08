1. Crea un documento de texto con cualquier editor o utiliza uno del que dispongas. 
2. Cifra este documento con alguna contraseña acordada con el compañero de al lado. 
3. Haz llegar por algún medio al compañero de al lado el documento que acabas de cifrar. 
4. Descifra el documento que te ha hecho llegar tu compañero de al lado. 
Creo el documento 
Lo cifro con GPG
Nos crea el documento.txt.gpg que esta cifrado
Ahora lo desciframos 

5. ¿Con qué algoritmo se ha cifrado el fichero? Vuelve a cifrar el fichero usando el algoritmo AES256. ¿Puedes hacer permanente esta configuración? 
Para saber el cifrado usamos  gpg --list-packets documento.txt.gpg 
Ya estamos usando AES256, en caso de querer usar otro algoritmo lo indicariamos en el comando :
gpg -c --cipher-algo BLOWFISH documento.txt, y si queremos que sea permanente, (creamos el fichero si no existe) en /home/kali/.gnupg/gpg.conf añadimos cipher-algo BLOWFISH

6. Instala gpg en windows (Gpg4win), repite el ejercicio en Windows. Puedes encriptar un mensaje en linux y desencriptarlo en windows y al contrario. 
Para windows debemos descargarlo de su sitio official https://gnupg.org/ e instalarlo.
Ahora con el archivo cifrado de kali que hemos traido a windows vamos a desencriptarlo, para eso usamos la aplicacion grafica,

Y nos devuelve el documento descifrado

7. openssl es otra herramienta que nos permite cifrar mensajes de forma simétrica, investiga como se realiza este ejercicio utilizando esta herramienta. 
Para usar openssl para encriptar el mismo archivo usamos el siguiente comando:
openssl enc -aes-256-cbc -salt -in documento.txt -out documento_encrypted.txt

Y para descifrar:
openssl enc -d -aes-256-cbc -in documento_encrypted.txt -out documento_decrypted.txt

Aqui vemos los documentos el encriptado y el desencriptado respectivamente


