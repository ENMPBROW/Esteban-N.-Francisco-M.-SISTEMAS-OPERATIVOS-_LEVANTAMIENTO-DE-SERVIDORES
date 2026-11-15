# Instalación y configuración del servicio FTP (vsftpd)

- sudo yum install vsftpd -y
- sudo systemctl status vsftpd
- sudo systemctl start vsftpd
- sudo systemctl enable vsftpd
- sudo systemctl status vsftpd
- ls /etc/vsftpd/
# Realizar una copia antes de editar o eliminar
- sudo cp /etc/vsftpd/vsftpd.conf /etc/vsftpd/vsftpd.conf.backup
- ls /etc/vsftpd/
- sudo nano /etc/vsftpd/vsftpd.conf
- Entramos al archivo, buscamos la línea chroot_local_user=YES y eliminamos el símbolo # para habilitarla. Luego presionamos Ctrl+O para guardar y Ctrl+X para salir.

# Verificación local del servicio FTP

- Entramos a la terminal de CentOS y verificamos el servicio con el comando: ftp localhost
- Si sale "orden no encontrada", el sistema pedirá instalar el cliente; confirmamos escribiendo (y) (si vuelve a pedir confirmación, escribimos (y) nuevamente).
- Ejecutamos otra vez: ftp localhost
- Nos pedirá el usuario (Name); ingresamos nuestro usuario del sistema y luego la contraseña. Al entrar correctamente aparecerá el mensaje: 230 Login successful.

# Apertura del puerto FTP en el firewall (MobaXterm)

- sudo firewall-cmd --list-all
- Aquí revisamos que solo tenemos activos los servicios http y ssh. Para habilitar el servicio ftp ejecutamos:
- sudo firewall-cmd --add-service=ftp --permanent
- sudo firewall-cmd --reload
- sudo firewall-cmd --list-all
- Verificamos nuevamente y ya aparecerá el servicio ftp habilitado.

# Creación y configuración del usuario exclusivo para FTP

- tail /etc/passwd ------->(sirve para verificar los usuarios recién creados en el sistema)
- sudo adduser usuario_ftp ------->(sirve para crear una nueva cuenta de usuario)
- sudo passwd epnbrow_ftp -------->(colocamos la contraseña para el usuario)
- sudo usermod -s /sbin/nologin usuario_ftp --------->(sirve para desactivar el acceso interactivo a la terminal para este usuario)
- sudo cat /etc/shells ------->(sirve para mostrar la lista completa de intérpretes de comandos válidos y permitidos)
- sudo nano /etc/shells ------->(abre el archivo de shells permitidos en el editor nano con permisos de superusuario)
- Entramos a la lista, agregamos en la parte final /sbin/nologin, y presionamos Ctrl+O y Ctrl+X para guardar y salir.

# Prueba de conexión local y desde MobaXterm

- ftp localhost
- Colocamos el usuario creado (usuario_ftp) y su contraseña; nos deberá salir el mensaje: 230 Login successful.
- Finalmente, abrimos MobaXterm,
- En MobaXterm creamos una nueva sesión seleccionando el servicio FTP, introducimos la dirección IP del servidor, el usuario, el puerto 21 y la contraseña que asignamos en la terminal de CentOS.

# Resultado a Obtener
<img width="1418" height="907" alt="image" src="https://github.com/user-attachments/assets/13366408-e56c-44ab-82f8-dc454b5f9cc5" />
