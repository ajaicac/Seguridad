# Práctica: Integridad, firmas y autenticación 
# Tarea 1: Firmas electrónicas (3 puntos)
 En este primer apartado vamos a trabajar con las firmas electrónicas, para ello te pueden ayudar los siguientes enlaces:
 • Intercambiar claves 
• Validar otras claves en nuestro anillo de claves públicas 
• Firmado de claves (Debian) 
GPG 
### 1. Manda un documento y la firma electrónica del mismo a un compañero. Verifica la firma que tu has recibido.  
Yo lo creare en un ubuntu y se lo enviare al kali linux 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/1.PNG)

## 2. ¿Qué significa el mensaje que aparece en el momento de verificar la firma? 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/2.PNG)

## 3. gpg: Firma correcta de "Pepe D " [desconocido] 
La firma del documento ha sido validada con la clave pública de "Pepe D" y su correo, [desconocido] indica el nivel de confianza que tienes en la clave pública utilizada para firmar,que en este caso, la clave no está firmada por una clave de confianza. 
## 4. gpg: ATENCIÓN: ¡Esta clave no está certificada por una firma de confianza! 
Este mensaje destaca que la clave pública utilizada para la firma no está respaldada por una firma de confianza. Esto significa que GPG no tiene información sobre la confianza que puedes tener en la autenticidad de la clave. 
## 5. gpg: No hay indicios de que la firma pertenezca al propietario. 
Sugiere que no hay pruebas adicionales de que la firma realmente pertenezca al propietario de la clave. Puede deberse a la falta de una cadena de confianza establecida. 
## 6. Huellas dactilares de la clave primaria: E8DD 5DA9 3B88 F08A DA1D 26BF 5141 3DDB 0C99 55FC 
Se trata de la secuencia de numeros y letras que representa la huella unica de cada clave que se usa para identifiarla

## 7. Vamos a crear un anillo de confianza entre los miembros de nuestra clase, para ello.
Añadir la clave de kali a un servidor , primero la muestro y des pues la subo ( como el primer servidro no iva, he probado otro)
gpg --keyserver keyserver.ubuntu.com --send-key C4AEF955329904BBBD7E0DD0B3C7AEED982E78AA

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/3.PNG)

Ahora me la descargo en kali

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/4.PNG)

Ahora firmamos la clave de ubuntu

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/5.PNG)

## 8. Muestra las firmas que tiene tu clave pública. 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/6.PNG)

## 9. Comprueba que ya puedes verificar sin “problemas” una firma recibida por una persona en la que confías. 
Ahora como tengo la clave de ubuntu al verificar el pdf, primero la exporto y despues la importo para verificar el pdf 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/6-1.PNG)

Y ahora podremos descifrar el archivo sin necesidad de contraseña 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/7.PNG)

## 10. Comprueba que puedes verificar con confianza una firma de una persona en las que no confías, pero sin embargo si confía otra persona en la que tu tienes confianza total. 

# Tarea 2: Correo seguro con evolution/thunderbird (2 puntos) 
Ahora vamos a configurar nuestro cliente de correo electrónico para poder mandar correos cifrados, para ello: 

## 1. Configura el cliente de correo evolution con tu cuenta de correo habitual 
Confirgurarlo es siguiente,siguiente y meter tu cuenta 

## 2. Añade a la cuenta las opciones de seguridad para poder enviar correos firmados con tu clave privada o cifrar los mensajes para otros destinatarios 
Para añdir la cuenta de seguridad miramos nuestra id publica:

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/8.PNG)

 Y la añadimos a evolution

 ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/9.PNG)

Y en 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/9-1.PNG)

## 3. Envía y recibe varios mensajes con tus compañeros y comprueba el funcionamiento adecuado de GPG 
Para enviar un correo cifrado a la hora de escribir un correo selecionamos en Firma: la firma que hemos añadido antes

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/10.PNG)

Y para cifrarlo activamos la opcion y le damos 

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/11.PNG)

# Tarea 3: Integridad de ficheros (1 punto) 
Vamos a descargarnos la ISO de debian, y posteriormente vamos a comprobar su integridad.
Puedes encontrar la ISO en la dirección: https://cdimage.debian.org/debiancd/current/amd64/iso-cd/. 

## 1. Para validar el contenido de la imagen CD, solo asegúrese de usar la herramienta apropiada para sumas de verificación. Para cada versión publicada existen archivos de suma de comprobación con algoritmos fuertes (SHA256 y SHA512); debería usar las herramientas sha256sum o sha512sum para trabajar con ellos. 
Esta parte es muy sencilla, descargamos la imagen y el archivo con los hashs, con el comando comprueba los hash segun el tipo de algoritmo que especifiquemos, como yo solo tengo una iso solo me da esa como valida

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/12.PNG)

Para  otro algoritmo lo mismo pero cambiando el algoritmo y su fichero de hash

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/13.PNG)


## 2. Verifica que el contenido del hash que has utilizado no ha sido manipulado, usando la firma digital que encontrarás en el repositorio. Puedes encontrar una guía para realizarlo en este artículo: How to verify an authenticity of downloaded Debian ISO images 

Despues de descargar el archivo SHA256SUMS.sign, importamos la firma:
  1. 1=Importaremos las claves publicas de debian
  2. 2=Verificamos clave
  3. 3=Comprobamos que ambos ficheros son iguales
Y lo mismo para los otros hash y su correspondiente firma

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/14.PNG)


# Tarea 4: Integridad y autenticidad (apt secure) (2 puntos) 
Cuando nos instalamos un paquete en nuestra distribución linux tenemos que asegurarnos que ese paquete es legítimo. Para conseguir este objetivo se utiliza criptografía asimétrica, y en el caso de Debian a este sistema se llama apt secure. Esto lo debemos tener en cuenta al utilizar los repositorios oficiales. Cuando añadamos nuevos repositorios tendremos que añadir las firmas necesarias para confiar en que los paquetes son legítimos y no han sido modificados. 
Busca información sobre apt secure y responde las siguientes preguntas: 
## 1. ¿Qué software utiliza apt secure para realizar la criptografía asimétrica? 
 El software de criptografía asimétrica GnuPG (GNU Privacy Guard) para verificar la autenticidad e integridad de los paquetes descargados desde los repositorios 
## 2. ¿Para que sirve el comando apt-key? ¿Qué muestra el comando apt-key list? 
 El comando apt-key se utilizaba anteriormente para manejar las claves GPG utilizadas por APT. Sin embargo, se ha desaconsejado su uso a favor de otras opciones más seguras. En su lugar, se recomienda utilizar el sistema de confianza de APT, que almacena las claves en /etc/apt/trusted.gpg.d/. 
## 3. En que fichero se guarda el anillo de claves que guarda la herramienta apt-key? 
El anillo de claves se guarda en el archivo /etc/apt/trusted.gpg 
## 4. ¿Qué contiene el archivo Release de un repositorio de paquetes?. ¿Y el archivo Release.gpg?. Puedes ver estos archivos en el repositorio http://ftp.debian.org/debian/dists/Debian10.1/. Estos archivos se descargan cuando hacemos un apt update. 
El archivo Release de un repositorio de paquetes contiene información sobre los paquetes disponibles, como sus versiones, arquitecturas y resúmenes hash. Este archivo es firmado digitalmente.
El archivo Release.gpg contiene la firma GPG del archivo Release, proporcionando autenticidad e integridad. Juntos, Release y Release.gpg se utilizan para garantizar la seguridad de los paquetes descargados.

## 5. Explica el proceso por el cual el sistema nos asegura que los ficheros que estamos descargando son legítimos. 
Cuando se ejecuta apt update, el sistema descarga los archivos Release y Release.gpg desde los repositorios. Luego, verifica la firma GPG utilizando la clave pública del repositorio almacenada localmente. Si la firma es válida y la clave se considera confiable, se procede a descargar la lista de paquetes y otros archivos. Este proceso garantiza que los archivos descargados son legítimos y no han sido modificados. 
## 6. Añade de forma correcta el repositorio de virtualbox añadiendo la clave pública de virtualbox como se indica en la documentación. 
  1. 1=Descargar e importar la clave pública de Oracle para VirtualBox
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo gpg --dearmor -o /usr/share/keyrings/virtualbox-archive-keyring.gpg
  2. 2=Configurar el repositorio de VirtualBox
echo "deb [signed-by=/usr/share/keyrings/virtualbox-archive-keyring.gpg] https://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list > /dev/null
  3. 3=Actualizar la lista de paquetes
sudo apt-get update

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/14-1.PNG)

Aqui podemos ver la clave de VirtualBox

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/3/15.PNG)


# Tarea 5: Autentificación: ejemplo SSH (2 puntos) 
Vamos a estudiar como la criptografía nos ayuda a cifrar las comunicaciones que hacemos utilizando el protocolo ssh, y cómo nos puede servir también para conseguir que un cliente se autentifique contra el servidor. Responde las siguientes cuestiones: 
## 1. Explica los pasos que se producen entre el cliente y el servidor para que el protocolo cifre la información que se transmite? ¿Para qué se utiliza la criptografía simétrica? ¿Y la asimétrica? 
Cuando un cliente se conecta a un servidor SSH, se sigue un proceso que incluye la negociación de algoritmos criptográficos. La criptografía simétrica se utiliza para cifrar la comunicación una vez que se ha establecido la conexión. La criptografía asimétrica se utiliza en la fase inicial para autenticar al servidor ante el cliente y, opcionalmente, para autenticar al cliente ante el servidor. 
**Criptografía simétrica:**
La criptografía simétrica solo utiliza una clave para cifrar y descifrar el mensaje, que tiene que conocer el emisor y el receptor previamente y este es el punto débil del sistema, la comunicación de las claves entre ambos sujetos, ya que resulta más fácil interceptar una clave que se ha transmitido sin seguridad 
**Criptografía asimétrica:**
La criptografía asimétrica se basa en el uso de dos claves: la pública (que se podrá difundir sin ningún problema a todas las personas que necesiten mandarte algo cifrado) y la privada (que no debe de ser revelada nunca). 

## 2. Explica los dos métodos principales de autentificación: por contraseña y utilizando un par de claves públicas y privadas. 
Contraseña: El usuario proporciona una contraseña para autenticarse en el servidor. Este método es común pero menos seguro.
Claves públicas y privadas: Se genera un par de claves (pública y privada) en el cliente. La clave pública se añade al archivo authorized_keys en el servidor. Durante la autenticación, el cliente demuestra poseer la clave privada correspondiente.

## 3. En el cliente para que sirve el contenido que se guarda en el fichero ~/.ssh/know_hosts? 

Las claves de máquinas se mantienen en etc/sshknownhosts y en el directorio del usuario ~/.ssh/knownhosts.
## 4. ¿Qué significa este mensaje que aparece la primera vez que nos conectamos a un servidor? 
**$ ssh debian@172.22.200.74 The authenticity of host '172.22.200.74 (172.22.200.74)' can't be established. ECDSA key fingerprint is SHA256:7ZoNZPCbQTnDso1meVSNoKszn38ZwUI4i6saebbfL4M. Are you sure you want to continue connecting (yes/no)? **

Este mensaje indica que la autenticidad del host no se ha establecido previamente. El cliente muestra la huella digital de la clave del servidor y pregunta al usuario si desea continuar la conexión. Si la huella digital coincide con la esperada, el usuario puede aceptar y la clave se almacenará en known_hosts. 

## 5. En ocasiones cuando estamos trabajando en el cloud, y reutilizamos una ip flotante nos aparece este mensaje: 
**$ ssh debian@172.22.200.74 @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ @ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @ @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY! Someone could be eavesdropping on you right now (man-in-the-middle attack)! It is also possible that a host key has just been changed. The fingerprint for the ECDSA key sent by the remote host is SHA256:W05RrybmcnJxD3fbwJOgSNNWATkVftsQl7EzfeKJgNc. Please contact your system administrator. Add correct host key in /home/jose/.ssh/knownhosts to get rid of this message. Offending ECDSA key in /home/jose/.ssh/knownhosts:103 remove with: ssh-keygen -f "/home/jose/.ssh/known_hosts" -R "172.22.200.74" ECDSA host key for 172.22.200.74 has changed and you have requested strict checking. **

Este mensaje aparece cuando la huella digital de la clave del servidor ha cambiado. Puede deberse a cambios en la configuración del servidor o a posibles ataques. Se aconseja al usuario que verifique la autenticidad del servidor y, si es necesario, actualice la clave en known_hosts mediante el comando ssh-keygen. 
## 6. ¿Qué guardamos y para qué sirve el fichero en el servidor ~/.ssh/authorized_keys? 
El archivo Authorized_keys en SSH especifica las claves SSH que se pueden usar para iniciar sesión en la cuenta de usuario para la que está configurado el archivo. Es un archivo de configuración muy importante, ya que configura el acceso permanente mediante claves SSH y necesita una gestión adecuada. 
