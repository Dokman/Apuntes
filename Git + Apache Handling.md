#H1
======
Servidor Git y enroutarlo a Apache

#H2
======
Si quieres usar un servidor [gitbucket](https://github.com/gitbucket/gitbucket)

#H3
======
Necesitamos un apache, si usamos xampp en windows viene todo pre-configurado entonces iremos a /xampp/apache/conf/extra/httpd-vhosts.conf

Y añadiremos estas lineas de código

<VirtualHost *:80>
	ProxyPreserveHost On
	ProxyPass /git http://localhost:8080/git
	ProxyPassReverse /gitbucket http://localhost:8080/git
</VirtualHost>

Recordemos que /git es como lo enrutamos, de series es /gitbucket

Para modificar a gusto nuestro gitbucket usaremos estos comandos:

java -jar gitbucket.war --port=8080 --prefix=/git --gitbucket.home=C:\GIT\data\ --host=localhost

donde

port : es el puerto que usaremos
prefix: es localhost/loquesea
host: es el servidor