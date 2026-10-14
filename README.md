# WannaCry 

<br>

<p align="justify"> El día 12 de mayo se produjo una campaña de ransomware a nivel mundial conocida como WannaCry, que se aprovechaba de una vulnerabilidad en el protocolo SMB v1, que fue corregida por Microsoft el 14 de marzo, pero solo en los equipos que instalaran la actualización. </p>

 

<p align="justify"> WannaCry atacó a todos los equipos que seguían sin parchear, dos meses después, se propagaba solo de un equipo a otro por el puerto 445 (SMB), sin que nadie tuviera que abrir un archivo ni hacer clic en nada.  </p>

 

<p align="justify"> El ransomware solicitó el pago de 300$ para recuperar la información cifrada, aunque nadie recuperó sus archivos pagando.  </p>

<br>

![wannacry](images/wannacry.png)
 

<br>
 

# Mittre attack 

<br>

![mitre](images/mitre.png)

<br>


<p align="justify">Podemos observar en esta tabla del Mittre Attack todas las tácticas y técnicas que realiza el WannaCry. </p>

 
 
### Scripting  

<br>
 
<p align="justify">Usa la táctica de scripting porque suelta archivos de Visual Basic, ejecuta archivos (.bat) y ejecuta scripts de Visual Basic. </p>

### Persistencia 

<br>

<p align="justify">Usa la táctica de persistencia por que modifica reglas de registro para guardar archivos en el directorio de inicio de Windows. </p>

### Escalada de privilegios 

<br>

<p align="justify">Usa la táctica de Escalada de privilegios por q consigue hacer un Process Howling en donde inyecta código malicioso en procesos suspendidos. </p>

<br>

# Análisis de malware en vivo 

![diagram](images/diagram.png)
 
<br>

<p align="justify">Al ejecutarse wannacrypt.exe en el ordenador infectado, se crean una gran cantidad de archivos .exe que contienen código arbitrario, que se ejecuta en el momento que se terminen de crear. </p>


 

<p align="justify">En la tercera columna de la imagen se pueden observar los archivos que crea y lo que hace cada uno. </p> 

 

<p align="justify">Aparte de ser persistentes, se ejecutan de nuevo cada vez que se inicie Windows, para evitar el borrado (se puede saber que se están creando porque saturan la CPU del ordenador y posteriormente el disco porque está escribiendo).  </p>

 

<p align="justify">Se puede ver en la imagen por ejemplo el taskmgr.exe que es un proceso legítimo de Windows, pero este lo enmascara y se hace pasar por el proceso para que se ejecute a la hora de lanzar el SO.  </p>

 

<p align="justify">Después una vez creados los ejecuta automáticamente dando lugar una encriptación completa de todos nuestros archivos originales que ya teníamos. </p>

 
Podemos observar cómo al ejecutarse, la CPU sube a niveles altísimos, esto es dado por el hecho de que se están creando los archivos. 

<br>

![process](images/process.png)

<br>

 

Cuando el fondo de pantalla es alterado, se confirma la encriptación completa de todos los archivos del disco. 

<br>
 
![wallpaper](images/anyrun1.png)

<br>


Uno de los últimos “.exe”, nos muestra como “recuperar” el acceso a nuestros archivos encriptados, pagando a una cartera de bitcoin. 

 
<br>
 
![wallpaper2](images/anyrun2.png)

<br>
 


Nos otorga 10 archivos desencriptados gratuitamente como demostración.  

 
<br>
 
![wallpaper3](images/anyrum3.png)

<br>
 

 

 

# Indicadores de Compromiso (IOCs) 

<br>

![wallpaper4](images/anyrum4.png)

<br>

Las direcciones ip que se observan en la imagen, son las que el malware realizaba peticiones, en la versión original del ataque de “WannaCry” este consultaba el dominio:  

iuqerfsodp9ifjaposdfjhgosurijfaewrwergwea.com 

Si no estaba activo(registrado) el dominio se ejecutaba el malware, se paró el ataque gracias a que una persona registró el dominio. 


Hashes de WannaCry extraídos de VirusTotal: 

<br>

![virustotal](images/virustotal1.png)
 
<br>
 

# VirusTotal para mirar telemetría y detección (subir el hash) 

<br>
 

En esta imagen podemos observar todos los procesos creados por el WannaCry. 

<br>
 
![virustotal1](images/virustotal2.png)
 
<br>

 

Estos son todos los comandos que ha realizado el WannaCry por detrás, unos de los comandos más críticos que realiza es la eliminación de una “shadowcopy” de Windows, que establece por predeterminado una política que ignora todos los errores al iniciar el sistema operativo de Windows y también podemos ver que desactiva toda opción de intentar la recuperación de esos archivos mediante copias de seguridad. 

 
<br>
 
![virustotal2](images/virustotal3.png)
 
<br>
 

En esta imagen nos muestra todos los procesos en los q ha inyectado código malicioso. 

 
<br>
 
![virustotal3](images/virustotal4.png)
 
<br>
 
 

En esta imagen podemos observar todos los archivos q ha abierto el WannaCry. 

 
<br>
 
![virustotal4](images/virustotal5.png)
 
<br>
 


Podemos observar todos los archivos en los que ha escrito WannaCry. 

 
<br>
 
![virustotal5](images/virustotal6.png)
 
<br>
 

 

Podemos observar todos los archivos en los que WannaCry ha modificado atributos. 

 
<br>
 
![virustotal6](images/virustotal7.png)
 
<br>
 

 

Podemos observar a todas las direcciones ip que ha hecho conexión el WannaCry. 


<br>
 
![virustotal7](images/virustotal8.png)
 
<br>

