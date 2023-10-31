# Tema 2

### 2. Analiza y describe los sistemas biométricos que actualmente se están utilizando, así como los estudios de implantación de nuevas tecnologías respecto a este campo

Tenemos los SB (Sistemas Biometricos) que llevan ya unos años implementados y popularizados dado que se usan masivamente en los teléfonos móviles.

- Reconocimiento facial: El reconocimiento facial utiliza cámaras para capturar y analizar rasgos faciales únicos. Grandes empresas tecnológicas, como Apple y Google, han implementado esta tecnología en sus dispositivos. Sin embargo, existen preocupaciones sobre la privacidad y la precisión, lo que ha llevado a un debate sobre su uso.
- Huellas dactilares: El escaneo de huellas dactilares es uno de los sistemas biométricos más antiguos y ampliamente utilizados. Se emplea en dispositivos móviles, sistemas de acceso, y la identificación de personas en aplicaciones gubernamentales. Es altamente preciso y aceptado por la mayoría de las personas.
- Reconocimiento de voz: El reconocimiento de voz se utiliza en sistemas de autenticación de voz y asistentes virtuales, como Siri de Apple y Alexa de Amazon. Está basado en las características únicas del habla de una persona, como la frecuencia y el tono de voz. Aunque es conveniente, la precisión puede verse afectada por factores ambientales y acentos.

Otros SB conocidos pero más de uso empresarial

- Escaneo de iris: El escaneo del iris es otro sistema biométrico utilizado en entornos de alta seguridad. La textura y patrón del iris son únicos para cada individuo. Se utiliza en aplicaciones como el control de acceso a edificios y aeropuertos. A pesar de su alta precisión, el costo de implementación puede ser un obstáculo.
- Reconocimiento de escritura: La verificación de firmas puede ser aplicable en áreas que requieren la automatización del flujo de trabajo, por ejemplo, en el caso bancario o judicial. Los algoritmos de reconocimiento de firmas se basan en algoritmos de reconocimiento de patrones o métodos matemáticos de análisis de curvas, ya que una firma puede representarse mediante un conjunto de puntos. Por lo tanto, a menudo utiliza la descomposición en series o la aproximación por curvas.
- Geometría de la mano: Este método biométrico utiliza la forma de la mano para autenticar la identidad. Debido al hecho de que los parámetros individuales de la forma de la mano no son únicos, es necesario utilizar varias características. Aunque la estructura de las articulaciones y los huesos son signos relativamente permanentes, la hinchazón de los tejidos o las contusiones en el brazo pueden distorsionar la estructura original. El problema de esta tecnología es que, incluso sin tener en cuenta la posibilidad de amputación, una enfermedad llamada artritis puede interferir enormemente en el uso de escáneres.

Nuevos SB que están surgiendo:

- Reconocimiento de venas de la palma de la mano: Este sistema biométrico se basa en la red vascular única de la palma de la mano. Se utiliza en aplicaciones de seguridad y acceso donde la higiene es importante, ya que no requiere contacto físico con la superficie de escaneo.
- Biometría del comportamiento: es un subcampo de la biometría que se enfoca en autenticar a individuos basándose en sus patrones únicos de comportamiento en lugar de características físicas estáticas. Esto implica el análisis de acciones como la escritura manuscrita, gestos y movimientos corporales, hábitos de tecleo, voz y patrones de navegación en dispositivos electrónicos. Cada persona tiene un comportamiento distintivo en estas áreas, lo que se utiliza para la autenticación.

## 6. Configura y automatiza la copia de seguridad en un entorno Linux de una estructura de directorios. Utiliza para ello el comando tar y el servicio crond – consideramos que la copia se realiza en el mismo equipo.

- Añado un disco a la máquina virtual de Linux, al que daré formato y montaré.
  
 ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/6/1.PNG)
 
- Verifico que el `tar` está instalado en el equipo, para instalarlo si no está.

   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/6/2.PNG)
  
- Creo un script que realiza la copia de seguridad del escritorio para que sea más rápido y el destino será el disco que he montado en la carpeta disco2.
  
   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/6/3.PNG)
  
- Le doy permisos de ejecución al script.
  
   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/6/4.PNG)
  
- Añado la ejecución al archivo `/etc/crontab` y reinicio el proceso cron.
  
   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/6/5.PNG)
  
- Y podemos ver cómo se ha creado una copia del escritorio.
  
   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/6/6.PNG)
  

## 7,9.
- Para hacer una copia en otro equipo vamos a retocar el script anterior usando rsync, ponemos la IP y ruta del equipo externo.
  
   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/7/1.PNG)
  
- Le damos permisos de ejecución
-  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/7/2.PNG)
- y lo añadimos al archivo crontab para posteriormente reiniciar el servicio.
  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/7/3.PNG)


- Pero aquí no termina, debemos darle la clave pública de SSH al otro equipo para que no nos pida contraseña, entonces la generamos y se la pasamos.
   
   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/7/4.PNG)

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/7/5.PNG)

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/7/6.PNG)

## 10.
- Usando lo que sabemos del ejercicio 6, podemos modificar el script para que use `dd`.
- 
  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/10/1.PNG)


## 11.
- Los servicios de AWS ofrecen características de copia de seguridad para proteger sus datos, como la replicación de Amazon S3, las instantáneas de Amazon EBS y Amazon RDS, las copias de seguridad de Amazon FSx y Amazon DynamoDB, y las instantáneas de AWS Storage Gateway. Todas las capacidades existentes de copia de seguridad por servicio siguen sin cambios. AWS Backup proporciona una forma común de administrar las copias de seguridad en todos los servicios de AWS, tanto en AWS como en las instalaciones. AWS Backup es un servicio centralizado que permite programar y monitorear las copias de seguridad, además de administrar su retención. AWS Backup es compatible con la funcionalidad de copia de seguridad existente que proporcionan S3, EBS, RDS, Amazon FSx, DynamoDB y Storage Gateway. AWS Backup ofrece capacidades de administración de copias de seguridad para los servicios de AWS con una funcionalidad de copia de seguridad integrada en AWS Backup, como Amazon EFS y DynamoDB. Algunas características son las políticas del ciclo de vida para trasladar copias de seguridad a un nivel de almacenamiento de bajo costo, almacenamiento y cifrado de copias de seguridad, lo cual es independiente de los datos de origen y de las políticas de acceso a las copias de seguridad.

## 12. 
- Lo mismo podemos simplemente modificar el script de los ejercicios anteriores para que utilice duplicity, con duplicity al ser una herramienta de copias de seguridad nos permite cifrar la copia y lo usaremos de esa forma.
- 
 ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/12/1.PNG)

 ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/12/3.PNG)

## 14. 
- Primero preparamos la máquina virtual, en mi caso un Ubuntu con dos discos, uno el del sistema operativo y otro al que irá dirigida la clonación.

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/1.PNG)
  
- Seleccionamos la primera opción.

 ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/2.PNG)
 
- Selecciono español.

 ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/3.PNG)
  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/4.PNG)
   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/5.PNG)
 
- Aquí hay varias opciones, yo que quiero clonar de un disco a otro elijo la segunda opción: device-device.

 ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/6.PNG)
 
- Yo voy a seleccionar el modo para principiantes.

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/7.PNG)
   
- Elegimos el disco que vamos a clonar.

   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/8.PNG)
  
- La ubicación donde se clonará.

   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/9.PNG)
  
- Para que sea más rápido voy a omitir la comprobación.

   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/10.PNG)
  
- Dejamos la tabla de particiones igual.

   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/11.PNG)
  
- Elijo que se apague cuando acabe.

   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/12.PNG)
- Y ahora quito el disco original para dejar solo la copia y al encender nos aparece ubuntu d
  
   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/13.PNG)

   ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/14/14.PNG)
  

## 22. 
- Preparamos la maquina que tendra el servidor openfiler, en mi caso seran 3 el disco principal y los de almacenamiento de 1 y 2 GB
  
  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/1.PNG)

- Durante la instalación nos saldrá  este cuadro para iniciar los discos

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/2.PNG)


- Desseleccionamos los discos para que la instalación solo se realice en que deseamos

    ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/3.PNG)


- Después de la instalación, al iniciar  secion añadimos las redes que tendrán acceso

    ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/4.PNG)

 
- Ahora nos vamos a Volumes>Block Devices > y le damos al disco que queramos dar formato

    ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/5.PNG)



- en mi caso le doy a los dos disco el mismo formato

    ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/6.PNG)


- Ahora vamos al grupo de volumenes para crear uno con los discos que queramos

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/7.PNG)

  
- Ahora vamos a añadir el volumen creado

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/8.PNG)

  
- es importante poner block (iSCSI...)

    ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/9.PNG)


- Ahora debemos ir a la pestaña SAN para habilitar el protocolo iSCSI

    ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/10.PNG)


-Ahora añadimos el volumen como target del protocolo iSCSI

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/11.PNG)



-Ahora nos aseguramos que el modo de transferencia sea de blockes 

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/12.PNG)


- Para añadirlo en Windows , abrimos Iniciador iSCSI y vamos
  
  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/13.PNG)


- Ponemos la ip y le damos a opciones avanzadas
  
  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/14.PNG)


- Lo ponesmos tal q asi

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/15.PNG)
  
![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/16.PNG)
  
- Ponemos el adaptador iSCSI, la ip de nuestra maquina y la del SAN

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/17.PNG)


- Y cuando abramos el administrador de discos nos aparecerá que tenemos un disco nuevo

  ![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/tema2/22/18.PNG)

  
