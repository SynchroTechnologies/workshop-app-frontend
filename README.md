# Workshop demo App Frontend

Aplicación Javascript de una sola página para la demostración del ciclo de vida DevOps.

## Descripción de la funcionalidad

- Cuando la página carga verifica si existe una cookie llamada "userId", con el texto del nombre del usuario que está utilizando el browser.
  * Si la cookie no existe, abre un popup dónde pregunta el nombre del usuario. Con el texto ingresado crea la cookie con validez de 5 días.
  * Si la cookie existe, lee el valor, que luego mostrará en pantalla, y continúa el cargado de la página.

- Una vez finalizada la carga, la página muestra información de la sesión: el userId, la fecha y hora, etc.

- La página presenta dos botones: "Enviar" y "Leer"
  * El botón "Enviar" se comunica con el backend y le pasa en formato Json la información del cuadro principal, para que el backend lo almacene en una base PostgreSQL.
  * El botón "Leer" se comunica con el backend y le pide los últimos 5 registros almacenados en la base PosrgreSQL, a lo que el backend responde con un Json, con los registros.

- Cada vez que se pulsa el botón "Enviar" se actualiza la fecha y hora, antes de mandar la información. La fecha y hora tiene una presición de 1 segundo.

- Cada vez que se pulsa el botón "Leer" se abre una ventana modal, por encima de la página principal, para mostrar los datos que se recibieron de la bas vía el backend.

## Instalación de la aplicación

La aplicación consiste de un archivo .html que contiene todo el código Javascript. Funciona completamente en el browser.

De lado del servidor solo requiere de algún web server standard que envíe el código a pedido del navegador.

Este servidor puede ser Nginx, por ejemplo. Con la configuración default es suficiente.

Su se utiliza Ubuntu Server, Nginx se instala con el siguiente comando:

```bash
> sudo apt install nginx
```

Una vez instalado, es necesario copiar el archivo .html y la imágen .jpeg en el directorio ```/var/www/html```

Finalmente, se debe iniciar el servicio. 

Si usas ```systemd```, puedes hacer  ```sudo systemctl start nginx```
Si no, puedes hacer ```sudo /etc/init.d/nginx start```

Nginx está configurado por defecto para escuchar peticiones en el puerto 80.

Antes de iniciar el servicio de Nginx, hay que modificar en la página la URL donde escucha el servicio de backend.

