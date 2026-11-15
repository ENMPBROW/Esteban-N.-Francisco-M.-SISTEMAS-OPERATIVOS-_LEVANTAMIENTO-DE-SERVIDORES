# Servicio NTP

- ip a (sirve para ver la dirección IP del servidor)
- sudo tee -a /etc/chrony.conf <<EOF
- Nos tendrá que salir el símbolo >, ejecutamos lo siguiente línea por línea:
<img width="507" height="96" alt="image" src="https://github.com/user-attachments/assets/c133d221-682a-429f-ab7d-27dbb93f988e" />


- sudo systemctl restart chronyd
- sudo firewall-cmd --add-service=ntp --permanent
- sudo firewall-cmd --reload

# Configuración en Windows (PowerShell como administrador)

- Abrimos PowerShell como administrador (clic derecho sobre el ícono de Windows y clic en Terminal/PowerShell como administrador).
- w32tm /config /manualpeerlist:"192.168.3.28,0x8" /syncfromflags:manual /reliable:YES /update  ----->(cambiar la IP del comando por la IP de tu servidor CentOS)


# Si sale error al ejecutar el comando anterior, iniciamos el servicio de hora en Windows y volvemos a intentar con los siguientes comandos:
- Set-Service -Name w32time -StartupType Automatic
- Start-Service -Name w32time
- w32tm /config /manualpeerlist:"192.168.3.28,0x8" /syncfromflags:manual /reliable:YES /update
- w32tm /resync /force
- w32tm /query /status

  
  <img width="658" height="480" alt="Captura de pantalla 2026-11-15 170918" src="https://github.com/user-attachments/assets/9dfc6b8e-9436-41e2-9f33-4a81c51c85c5" />

# Comprobación del servicio NTP en Windows

- Presiona las teclas Windows + I para abrir la Configuración, entra al apartado Hora e idioma y haz clic en Fecha y hora.
- Desactiva la opción Establecer hora automáticamente y cambia la hora o fecha actual de forma manual para desconfigurarla.
- Luego, presiona Windows + R, escribe <span translate="no">timedate.cpl</span> y presiona Enter para abrir la ventana clásica de Fecha y hora.
- Ve a la pestaña Hora de Internet, haz clic en Cambiar la configuración e ingresa la dirección IP de tu servidor CentOS (192.168.18.198).
- Haz clic en Actualizar ahora y luego en Aceptar; si la hora vuelve a sincronizarse automáticamente con la de tu servidor, confirmarás que el servicio NTP funciona correctamente.
  
  # Resultados a Obtener
  <img width="477" height="327" alt="Captura de pantalla 2026-11-15 171412" src="https://github.com/user-attachments/assets/1d30aa8b-eb14-43a2-9dd7-a2ab1a5ea79c" />
  <img width="423" height="511" alt="image" src="https://github.com/user-attachments/assets/0f3eb511-f36a-4bb8-adae-53937810111e" />

  


