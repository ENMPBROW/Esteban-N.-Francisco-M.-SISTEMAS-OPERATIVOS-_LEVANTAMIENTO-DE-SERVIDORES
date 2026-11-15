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

