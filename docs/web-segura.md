# Práctica 3: Web segura

En esta práctica he realizado la configuración de una **web segura mediante HTTPS** utilizando NGINX y un certificado digital.

## 1. Creación del certificado digital

He creado un certificado de firma digital para poder utilizar HTTPS en el servidor.

También he comprobado que el certificado se ha creado correctamente. Aunque este proceso se puede automatizar mediante un script, en mi caso lo he realizado manualmente.

## 2. Consulta del certificado

He consultado el certificado para comprobar sus datos, como la provincia donde se ha tramitado, la fecha de caducidad y otra información relacionada.

## 3. Configuración de NGINX

He creado una copia del fichero `default` dentro de:

```text
/etc/nginx/sites-available

Después he creado y modificado la configuración del sitio seguro para utilizar el certificado digital y habilitar HTTPS.

## 4. Creación de la página web
He creado la carpeta:
/var/www/segur

Dentro de ella he creado un archivo index.html con el contenido de la página web.

La página muestra que se trata de una web estática HTTPS, indicando que es un sitio seguro local y que utiliza un servidor NGINX.

## 5. Habilitación del sitio
He habilitado el sitio mediante un enlace desde sites-available hacia sites-enabled.

## 6. Aplicación de los cambios
He comprobado que la configuración de NGINX es correcta y he recargado el servicio para aplicar los cambios.
sudo nginx -t
sudo systemctl reload nginx

La configuración se ha aplicado correctamente.

## 7. Comprobación de la página HTTPS
Finalmente, he accedido a la página mediante HTTPS.
El navegador muestra una advertencia debido a que se trata de un certificado local, por lo que he continuado al sitio desde las opciones avanzadas.
Después de aceptar la advertencia, he comprobado que la página web funciona correctamente mediante HTTPS.

La práctica recoge la creación del certificado, la configuración de NGINX, la creación de la web y la comprobación final mediante HTTPS
