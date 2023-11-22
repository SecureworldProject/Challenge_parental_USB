# Challenge_parental_USB

Challenge que genera una clave en funci�n del si un determinado dispositivo extra�ble, denominado "dispositivo parental", se encuentra conectado al equipo.

Se considera parental ya que permite comprobar que, por ejemplo, el USB del padre/madre o de un empleado de la oficina se encuentre conectado

## Prerrequisitos

Instalar la librer�a `win32file` con `pip install pywin32`


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

Todas las funciones y la l�gica del challenge se encuentran en el fichero parental_usb_challenge.py, el cual es un programa en python que contiene toda la l�gica del challenge. La funci�n principal dentro del fichero que gestiona toda la l�gica del challenge es locate_usb(), la cual devuelve la lista de dispositivos extra�bles conectados.

Primero hay que llamar al m�todo win32file.GetLogicalDrives() para obtener la lista de dispositivos l�gicos. Despu�s, mediante el m�todo GetDriveType() se obtiene el tipo de dispositivo l�gico y posteriormente win32file.DRIVE_REMOVABLE para comprobar que es un dispositivo extra�ble. Con la lista definitiva, se almacena en un array y se comprueba si el dispositivo objetivo se encuentra en la lista o no. Finalmente, se genera una clave en funci�n de si est� conectado o no.