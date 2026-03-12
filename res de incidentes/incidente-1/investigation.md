# Investigation:

el usuario Roger Fedora, tiene uso reciente de un archivo llamado "MRUListEx" dentro de la franja horaria indicada en la tarea (12:05 a 12:45 19/11/2022)

data interna del archivo:

04-00-00-00
0C-00-00-00
0B-00-00-00
0A-00-00-00
09-00-00-00
08-00-00-00
07-00-00-00
06-00-00-00
02-00-00-00
05-00-00-00
01-00-00-00
03-00-00-00
00-00-00-00
FF-FF-FF-FF

esta lista contiene el orden de uso reciente de entradas del registro. 


tanto HKCU\Software\Microsoft\Windows\CurrentVersion\Run como HKCU\Software\Microsoft\Windows\CurrentVersion\Policies  
No contienen información reelevante.


# Jump List

utilizando el JLECmd extraemos la evidencia de erchivos abiertos por aplicaciones:

comando: JLECmd -d <directorio> --csv <output>

para leerlo utilizaremos EZViewer
No se encuentran datos importantes para la investigación en 

C:\Users\<user>\AppData\Roaming\Microsoft\Windows\Recent\AutomaticDestinations

y en

C:\Users\<user>\AppData\Roaming\Microsoft\Windows\Recent\CustomDestinations




# Revisión chrome

dentro de C:\Users\THM-RFedora\AppData\Local\Google\Chrome\User Data

no se encuentran datos de descargas que alimenten la investigación


# Revisión USB

Analizando el hive SYSTEM no se encuentra información sobre el uso de dispositivos externos como usb.



# SYSTEM HIVE

HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
Hallazgo! Se detecta que el programa 7-Zip se encontraba en el sistema, y fué desinstalado dentro del rango horario (12:05 -> 12:45)
el horario de desinstalación es cerca de las 12:09:33



HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths
Hallazgo! Se detecta la existencia del directorio: C:/Program Files/7Zip y el executable homonimo dentro de las apps.


Con la nueva información retomamos NTUSER

dentro de software encotramos informacion sobre el programa antes mencionado (7zip) el mismo confirmamos que abrió un archivo con caracter de secreto
en la siguiente ruta: C:\Program Files (x86)\Windows Media Player\Skins\tophatsecret\

Analizando la carpeta se encuentra que el archivo 7zip continua dentro de la misma, permitiendo así armar el siguiente time-line:

12:09:33 → modificación de registry de 7-Zip
12:10:xx → navegación de carpeta tophatsecret
12:10:21 → actividad sobre continental.png
12:12:35 → actividad sobre launchcodes.txt


como conclusión provisional podemos afirmar:

El sistema fue utilizado entre 12:05 y 12:45
7-Zip fue utilizado para acceder a la carpeta tophatsecret
Se creó o manipuló un archivo comprimido (.7z), lo que sugiere preparación para exfiltración de datos

flujo probable:

7zip abre continental.7z
↓
se listan los archivos internos
↓
se extraen archivos
↓
se preparan para exfiltración


# Autopsy

Haciendo uso de la herramienta leemos el disco local, navegando a la carpeta descargas del usuario donde se presenta la exfiltración encontramos la descarga del archivo 7z2201-x64.exe a las 12:09:19 y con fecha 2022-11-19 (UTC)


# Ezviewer + Jumplist
con la nueva información encontramos el archivo.txt lauchcode C:\Users\THM-RFedora\Desktop\launchcode.txt
el mismo fué abierto 2 veces luego de su creación en el escritorio