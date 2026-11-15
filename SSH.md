# Levantamiento de Servidores

**Integrantes:** Francisco Morillo y Esteban Nievecela

Instalación y activación del servicio SSH

Antes de cambiar el puerto, asegúrate de tener el servidor actualizado y el demonio SSH instalado y en ejecución en CentOS.

# Instalar, Iniciar y Verificar el Servicio:

- sudo dnf install openssh-server -y
- sudo systemctl enable --now sshd
- sudo systemctl status sshd

# Cambiar el puerto 22 a uno personalizado

- sudo nano /etc/ssh/sshd_config
- Buscamos la línea que diga #Port 22 ,borramos el # quedando así: Port 2237
- Crtl + O Enter, Crtl + X Enter --->para guardar y salir
- `sudo semanage port -a -t ssh_port_t -p tcp 2237`
- sudo firewall-cmd --permanent --add-port=2237/tcp
- sudo firewall-cmd --reload
- sudo systemctl restart sshd
- sudo systemctl status sshd
# Comando para entrar al servidor de forma remota por el puerto 2237.
- ssh usuario@ip_del_servidor -p 2237
#  verificacion de la correcta conexión con Mobaxtrem
- Nos pedirá ip se ocupa el comando en CentOS ----> ip a

- Usuario ----> efnievecela

- Puerto -----> Personalizado en mi caso : 2237

- contraseña----> con la que inicias en CentOS


  <img width="577" height="186" alt="image" src="https://github.com/user-attachments/assets/c7447515-4ee3-41cf-93d6-1b194b0bf4c3" />
