# Funcionalidades Nginx
Veremos a continuación algunas de las funcionalidades de _nginx_

## Habilitar _HTTPS_
Para ello primero debemos de realizr los siguientes comandos
~~~
mkdir /etc/nginx/certificate
cd /etc/nginx/certificate

openssl req -new -newkey rsa:4096 -x509 -sha256 -days 365 -nodes -out nginx-certificate.crt -keyout nginx.key
~~~
Despues de realizar el comando de _openssl_ nos solicitará introducir unos datos y nos genererará dos certificados, despues tendremos que modificar nuestro fichero de configuración para que quede de la siguente manera:
~~~
server {

        listen 443;
        server_name tudominio.com;

        root         /usr/share/nginx/html;
        index index.html index.htm;

        ssl on;
        ssl_certificate /etc/nginx/certificate/nginx-certificate.crt;
        ssl_certificate_key /etc/nginx/certificate/nginx.key;
}
~~~
Una vez realizado los cambiaos tendremos que reiniciar nuestro servicio, en este caso con el comando:
~~~
service nginx restart
~~~

### Resultado
Una ves realizado el reinicio y no ha dado problemas solo nos queda entrar a traves de _HTTPS_ y verificar que funciona, una vez nos conectemos ya tendremos nuestro _HTTPS_ configurado

![resultado](https://github.com/Joel1747/FuncionalidadesNginx/blob/master/imagenes/Captura%20de%20pantalla%20de%202023-02-09%2017-23-53.png)

