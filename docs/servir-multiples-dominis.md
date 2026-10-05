# Práctica 2: Servir múltiples dominios

En esta práctica he realizado la configuración de **NGINX para servir múltiples dominios**.

## 1. Copia y configuración de los sitios

He realizado una copia del fichero `default` de NGINX para poder crear y modificar las configuraciones de las páginas web.

He creado y configurado los ficheros correspondientes a:

- `pagina1.com`
- `pagina2.com`

También he eliminado la configuración `default` de la directiva `listen` para evitar problemas de funcionamiento.

## 2. Creación de las carpetas de las páginas

He creado las dos carpetas correspondientes para alojar las páginas web:

```text
/var/www/pagina1
/var/www/pagina2

Después he modificado el index.html de cada página para añadir su contenido correspondiente.

También he añadido un archivo script.js con una función JavaScript para comprobar que funciona correctamente.

## 3. Activación de los dos sitios
He activado los dos sitios mediante enlaces simbólicos desde sites-available hacia sites-enabled.
De esta forma, las dos páginas quedan habilitadas en NGINX.

## 4. Comprobación y reinicio de NGINX
He comprobado que la configuración de NGINX es correcta y posteriormente he recargado el servicio:
sudo nginx -t
sudo systemctl reload nginx

La configuración se ha realizado correctamente.


## 5. Configuración del fichero hosts
He modificado el fichero hosts para asociar los dominios con la dirección IP del servidor.
He añadido las entradas correspondientes para:
- www.pagina1.com
- www.pagina2.com


## 6. Comprobación de las páginas
Finalmente, he comprobado desde el navegador que los dos dominios funcionan correctamente.
La página pagina1.com se muestra correctamente y la página pagina2.com también funciona, incluyendo la comprobación de JavaScript.

La práctica documenta la configuración de los dos sitios, la activación de NGINX y la comprobación final de ambas páginas. :chatgpt-content-reference{index="0"}
