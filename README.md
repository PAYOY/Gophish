# Gophish
<p align="center">
<img src=Imagenes/gophish.png width="450" height="200">
</p>

Guia para desplegar y configurar Gophish para campañas de Phishing, incluyendo cómo implementar el certificado para enviar los enlaces de Phishing con HTTPS.

****
# Primeros pasos
Debemos de instalar el lenguaje de programación Go, el cual podemos descargar desde los repositorios de APT en Ubuntu Server.

```bash
sudo apt install golang
```
Ahora debemos de tener asociado nuestra IP pública a nuestro nombre de dominio, esto es importante para poder generar los certificados mediante Certbot.
Una vez que nuestra IP resuelva a nuestro DNS procedemos con la instalación de Apache y Certbot
Para instalar Apache realizamos lo siguiente:

```bash
sudo apt install apache2
```
Instalamos Certbot

```bash
sudo apt install certbot python3-certbot-apache2
```
Teniendo lo anterior, procedemos con la generación de nuestro certificado.

```bash
certbot certonly --standalone --certname <nombre> -d <nombre de tu dominio> -m <correo> --agree-tos --noninteractive
```
Por defecto Certbot nos guardará los certificados en la siguiente ruta:
```bash
/etc/letsencrypt/live/<dominio>/fullchain.pem
/etc/letsencrypt/live/<dominio>/privkey.pem
```
Para instalar Gophish debemos de descargarnos el comprimido.

```bash
wget https://github.com/gophish/gophish/releases/download/v0.12.1/gophish-v0.12.1-linux-64bit.zip #Puedes probar con curl también
sudo unzip gophish-v0.12.1-linux-64bit.zip
```

Eso es todo para poder comenzar con la configuración de nuestro Gophish.


