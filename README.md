# Challenge_parental_USB

Challenge que genera una clave en función del si un determinado dispositivo extraíble, denominado "dispositivo parental", se encuentra conectado al equipo.


## Prerrequisitos

Instalar la librería `win32file` con `pip install pywin32`


ejemplo de configuracion json
```json
{
	"FileName": "parental_usb_challenge.dll",
	"Description": "Challenge that generates a key based on if a device is connected or not to the computer",
	"Props": {
		"validity_time": 3600,
		"refresh_time": 3000
	},
	"Requirements": "none"
}
```

## Funcionamiento

Todas las funciones y la lógica del challenge se encuentran en el fichero parental_usb_challenge.py, el cual es un programa en python que contiene toda la lógica del challenge. La función principal dentro del fichero que gestiona toda la lógica del challenge es locate_usb(), la cual devuelve la lista de dispositivos extraíbles conectados.

Primero hay que llamar al método win32file.GetLogicalDrives() para obtener la lista de dispositivos lógicos. Después, mediante el método GetDriveType() se obtiene el tipo de dispositivo lógico y posteriormente win32file.DRIVE_REMOVABLE para comprobar que es un dispositivo extraíble. Con la lista definitiva, se almacena en un array y se comprueba si el dispositivo objetivo se encuentra en la lista o no. Finalmente, se genera una clave en función de si está conectado o no.