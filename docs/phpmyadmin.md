# Pràctica 4 — phpMyAdmin
## Objetivo

El objetivo de la práctica ha sido instalar y configurar phpMyAdmin para poder acceder a él mediante Nginx, asignarle un dominio local, configurar el acceso mediante contraseña y, finalmente, proteger la instancia de phpMyAdmin. La práctica corresponde a Implantación de Sistemas Operativos, 2º ASIX.     Pràctica 4 phpmyadmin - Josep C…

1. Instalación de phpMyAdmin
Primero se realizó la instalación de phpMyAdmin en el sistema.
Durante la instalación apareció una pantalla en la que se debía seleccionar el servidor web. En este caso no se seleccionó Apache ni ningún otro servidor, ya que phpMyAdmin se iba a configurar manualmente para funcionar con Nginx.
Por ello, en la pantalla de selección se pulsó TAB y se continuó con la instalación.
Importante: phpMyAdmin queda instalado, pero la configuración para que sea accesible mediante Nginx se realiza posteriormente de forma manual.


2. Configuración de phpMyAdmin para funcionar con Nginx
Una vez instalado phpMyAdmin, se configuró Nginx para que pudiera servir la aplicación.
Primero se copió el fichero de configuración default de Nginx para crear una configuración específica para phpMyAdmin.
sudo cp default phpadmin

De esta forma se creó un nuevo fichero llamado phpadmin dentro de:
/etc/nginx/sites-available/

La finalidad era disponer de un sitio independiente para phpMyAdmin.

3. Configuración del fichero de Nginx
Después se editó el fichero de configuración creado anteriormente:
/etc/nginx/sites-available/phpadmin

Dentro del fichero se introdujo la configuración necesaria para que Nginx pudiera servir phpMyAdmin.
Un punto especialmente importante fue configurar correctamente la directiva root.
La ruta indicada en root tiene que corresponder con la ubicación donde está instalado phpMyAdmin. Si esta ruta no es correcta, Nginx no podrá encontrar los archivos de phpMyAdmin y la aplicación no funcionará.
La configuración se puede observar en la figura 3 de la página 4.     Pràctica 4 phpmyadmin - Josep C…

4. Activación del sitio en Nginx
Una vez terminada la configuración, se activó el nuevo sitio mediante un enlace simbólico desde sites-available hacia sites-enabled.
El objetivo es que Nginx tenga habilitada la configuración de phpMyAdmin.
sudo ln -s /etc/nginx/sites-available/phpadmin /etc/nginx/sites-enabled/

Después se comprobó que el enlace aparecía correctamente dentro de sites-enabled.

5. Comprobación de la configuración de Nginx
Antes de reiniciar o recargar Nginx, se comprobó que la configuración no tuviera errores.
Para ello se ejecutó:
sudo nginx -t

El resultado indicó que la configuración era correcta:
syntax is ok
test is successful

Una vez comprobada la configuración, se recargó Nginx:
sudo systemctl reload nginx

Con esto se aplicaron los cambios realizados sin necesidad de detener completamente el servidor.

6. Configuración del fichero hosts
Para poder acceder a phpMyAdmin utilizando un dominio local, se modificó el fichero:
/etc/hosts

En este fichero se añadió el dominio correspondiente a phpMyAdmin asociándolo con la dirección IP del servidor.
De esta forma, el sistema puede resolver el nombre del dominio local hacia la máquina donde está funcionando Nginx.

7. Comprobación del acceso a phpMyAdmin
Una vez configurados Nginx y el fichero hosts, se realizó una prueba desde el navegador.
Se accedió al dominio configurado y apareció correctamente la pantalla de inicio de sesión de phpMyAdmin.
Esto demuestra que:

    1. phpMyAdmin estaba instalado.
    2. Nginx estaba correctamente configurado.
    3. El dominio local resolvía correctamente.
    4. Nginx podía servir phpMyAdmin.
    5. La aplicación era accesible desde el navegador.

8. Permitir el acceso mediante contraseña al usuario root de MySQL/MariaDB
El siguiente paso fue configurar el acceso mediante contraseña para el usuario root de la base de datos.
Primero se entró en MariaDB/MySQL y se comprobaron los usuarios existentes.
Posteriormente se modificó la contraseña del usuario root.
En la práctica se utilizó:
ALTER USER 'root'@'localhost' IDENTIFIED BY 'MySQL-alumno-2026!';

Después se volvió a consultar la información de los usuarios para comprobar que el cambio se había realizado correctamente.
Esto aparece en la página 6, en las figuras 7 y 7.1.     Pràctica 4 phpmyadmin - Josep C…
Importante
Durante la práctica se indica que el comando proporcionado en Aules para cambiar la contraseña no era compatible con MariaDB.
Por ese motivo se utilizó el comando:
ALTER USER 'root'@'localhost' IDENTIFIED BY 'MySQL-alumno-2026!';


9. Creación de un usuario dedicado para MySQL
Además del usuario root, se creó un usuario específico para poder acceder a MySQL/MariaDB.
En la práctica se creó el usuario:
admin

y se le asignaron los permisos correspondientes.
La creación del usuario se realizó desde MariaDB y posteriormente se comprobó que podía utilizarse para acceder a phpMyAdmin.

10. Comprobación del usuario admin
Una vez creado el usuario dedicado, se comprobó su funcionamiento iniciando sesión en phpMyAdmin con sus credenciales.
El acceso se realizó correctamente y se pudo entrar en la interfaz de administración de phpMyAdmin.
La figura 9 de la página 7 muestra la entrada a phpMyAdmin utilizando las credenciales del usuario admin.     Pràctica 4 phpmyadmin - Josep C…
Por tanto, en este punto ya se había conseguido:

 Nginx
   ↓
phpMyAdmin
   ↓
MariaDB/MySQL
   ↓
Usuario admin

11. Protección de la instancia de phpMyAdmin
Como último paso se aseguró el acceso a la instancia de phpMyAdmin mediante una segunda autenticación.
Para ello se instaló Apache, ya que se necesitaba disponer de la herramienta htpasswd.
La instalación se realizó mediante:
sudo apt install apache2-utils

Esto permitió utilizar htpasswd para crear un fichero de usuarios y contraseñas que posteriormente ser utilizada

12. Creación del usuario mediante htpasswd
Una vez instalada la herramienta, se creó un usuario para proteger el acceso a phpMyAdmin.
Se utilizó:
sudo htpasswd -c /etc/nginx/.htpasswd admin

El comando solicita una contraseña y su confirmación.
Como resultado se creó el fichero:
/etc/nginx/.htpasswd

Este fichero contiene las credenciales que Nginx utilizará para realizar la autenticación.

13. Configuración de la autenticación en Nginx
Finalmente se modificó nuevamente la configuración del sitio de phpMyAdmin en Nginx.
Se añadieron las siguientes directivas:
- auth_basic "Accés restringit";
- auth_basic_user_file /etc/nginx/.htpasswd;

La primera línea establece el mensaje que aparecerá al solicitar las credenciales.
La segunda indica a Nginx dónde se encuentra el fichero que contiene los usuarios autorizados:
/etc/nginx/.htpasswd

14. Recarga de Nginx y aplicación de la configuración
Después de modificar la configuración, se recargó Nginx para aplicar los cambios:
sudo nginx -s reload

También se realizaron las acciones necesarias para proteger correctamente el fichero de contraseñas:
sudo chmod 700 /etc/nginx/.htpasswd
sudo chown root:www-data /etc/nginx/.htpasswd

Con esto se aplicaron los cambios y se protegió el fichero utilizado para la autenticación.
La comprobación aparece en la figura 10.3 de la página 8.     Pràctica 4 phpmyadmin - Josep C…
Resultado final
Al terminar todos los pasos se consiguió tener phpMyAdmin funcionando mediante Nginx y protegido mediante autenticación.
El proceso completo realizado fue:
    1. Instalar phpMyAdmin
        ↓
    2. No seleccionar Apache/Nginx durante el instalador
        ↓
    3. Configurar phpMyAdmin manualmente para Nginx
        ↓
    4. Crear el sitio phpadmin en sites-available
        ↓
    5. Configurar la ruta de phpMyAdmin
        ↓
    6. Activar el sitio con un enlace simbólico
        ↓
    7. Comprobar Nginx con nginx -t
        ↓
    8. Recargar Nginx
        ↓
    9. Configurar /etc/hosts
        ↓
    10. Comprobar el acceso desde el navegador
        ↓
    11. Configurar contraseña para root de MariaDB
        ↓
    12. Crear el usuario admin
        ↓
    13. Comprobar el acceso con admin
        ↓
    14. Instalar apache2-utils
        ↓
    15. Crear .htpasswd con htpasswd
        ↓
    16. Añadir auth_basic a Nginx
        ↓
    17. Recargar Nginx
        ↓
    18. Proteger el fichero .htpasswd
        ↓
    19. phpMyAdmin funcionando y protegido
