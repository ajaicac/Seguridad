# Ejercicios 

## 1. Selecciona un documento pdf y encríptalo y fírmalo (opción --sign). Envíalo a un compañero, que debe en primer lugar verificar la firma y posteriormente descifrar el documento. 
Antes de cifrar debemos general la clave para firmar:

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/2/1.PNG)

Ciframos el documento con firma con el siguiente comando:
**gpg --sign --encrypt -r agustin documento.pdf**

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/2/2.PNG)

Ahora comprobamos que tiene la firma con :
**(Esto solo funciona si el documento no ha sido encriptado por lo que hay que hacer :**
**└─$ gpg --sign -r agustin documento.pdf   para usar --verify y que funcione )**

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/2/3.PNG)

Para descifrar usamos:
**└─$ gpg --decrypt documento.pdf.gpg > documento_recibido.pdf**

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/2/4.PNG)

## 2. Realiza el mismo ejercicio pero obteniendo una firma ASCII. 
## 3. Ahora sólo queremos firmar un documento. Firma un documento (opción --detach-sign). A continuación envía el documento original y la firma a un compañero para que verifique que el documento está firmado por tí. 

Encriptar el pdf

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/2/5.PNG)

Comprobar la firma

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/2/6.PNG)

Desencriptar documento

![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/Tema4/2/7.PNG)
