# Comandos utilizados para instalar y configurar el servidor web HTTPD

- sudo dnf install httpd 
- httpd -v
- sudo systemctl status httpd
- sudo systemctl start httpd
- sudo systemctl status httpd
- sudo firewall-cmd --list-all
- sudo firewall-cmd --add-service=http --permanent
- sudo firewall-cmd --reload
- sudo firewall-cmd --list-all

# Recomendacion
Antes de modificar o eliminar siempre se tiene que realizar una copia se seguridad
- sudo cp /usr/share/httpd/noindex/index.html /usr/share/httpd/noindex/index.html.backup
# Entrar y modificar
- sudo nano /usr/share/httpd/noindex/index.html
- Para guardar los cambios crtl+O , para salir crtl+x


# Agregar imagen de la Universidad de Cuenca

1. Descargamos directamente la imagen desde CentOS, buscando el logo de la Universidad de Cuenca.
- Otra alternativa, tomamos la imagen descargada en Windows y la transferimos mediante el servicio FTP, agregándola en el apartado de imágenes en CentOS.

2. Luego en la terminal ejecuta los siguientes comandos:

- sudo cp ~/Imagenes/"LOGO.UCUENCATEC.png" /var/www/html/ucuenca_tec.png
- sudo chmod 644 /var/www/html/ucuenca_tec.png
- sudo chown apache:apache /var/www/html/ucuenca_tec.png
- sudo restorecon -v /var/www/html/ucuenca_tec.png
- ls -la /var/www/html/ucuenca_tec.png
- sudo nano /usr/share/httpd/noindex/index.html


3. <img src="/noindex/images.jpg" alt="UCUENCATEC" style="width:110px; margin-left:15px; vertical-align:middle;"> 

3.1 <img width="1550" height="362" alt="image" src="https://github.com/user-attachments/assets/2b97b190-c209-4688-abee-023426ff9d65" />

# Resultado a Obtener
![Uploading image.png…]()



