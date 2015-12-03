title: Express
tags: []
categories:
  - Módulo 2
  - Express
description: muy bonito
date: 2015-11-07 20:51:00
---
### RUTAS / ROUTING EN CON NODEJS Y EXPRESS

Para añadir más páginas a nuestro sitio, necesitamos más rutas. Podemos hacerlo usando Express Router, que ya viene integrado en Express. Esta entrada será un tanto bestia ya que el manejo de las rutas será una parte importante de todas las aplicaciones que hagamos de ahora en adelante.

Esta es la manera de crear las rutas básicas para sitios web, y también la forma en la que finalmente construiremos  nuestras APIs RESTful que utilizará una app frontend en Angular. Así que, sin más dilación procedemos a enrutar (que palabra más fea señores, usaremos routing a partir de ahora).



#### EXPRESS ROUTER

¿Qué es exactamente Express Router? Puedes considerarlo como una mini aplicación de express sin tantas funcionalidades, solo routing. No incorpora vistas o configuraciones, pero  nos proporciona  una routing API con funciones como .use(), .get(), .param(), y route(). Echaremos un vistazo al significado de todo esto.

Hay varias formas de usar routing. Ya usamos uno de sus métodos cuando creamos la página de inicio en la anterior entrada usando ‘app.get(‘/’, …). Veremos otros métodos para hacer más secciones de nuestro sitio y comentaremos el por qué y cuando usarlos.

EJEMPLO DE LAS CARACTERÍSTICAS DE UNA APLICACIÓN

Estas son las principales características que añadiremos  a nuestra aplicación actual:

Rutas básicas (ya hemos tenemos hecha la página principal)
Rutas de otras secciones del sitio (parte del Admin/Administrador con sus sub-rutas)
Middleware para registros de peticiones (log request) en consola
Ruta con Parámetros (http://localhost:1337/usuarios/darthvader)
Ruta Middleware para Parámetros, para validar parámetros específicos
Rutas de inicio de sesión (login routes) haciendo GET y POST
Validar un parámetro que se pasa a una ruta concreta
¿Qué es el Middleware? El Middleware se invoca ente la petición de un usuario y la respuesta final. Es todo lo que ocurre desde que sale una solicitud en lado del cliente hasta que llega a nuestra lógica de la ruta en el servidor. Volveremos sobre este concepto cuando tengamos que registrar los datos de cada petición por la consola/terminal (log data). Un usuario solicitará la página, lo registramos en la consola (middleware) y después enviaremos la respuesta con la página solicitada. Próximamente, más sobre el middleware.
Como hemos hecho hasta ahora, tendremos nuestras rutas en el archivo server.js. No necesitaremos hacer cambio alguno en nuestro package.json puesto que ya viene todo instalado con Express.

RUTAS BÁSICAS / BASIC ROUTES

Ya definimos nuestra ruta básica en la página de inicio. Express nos deja definir las rutas con nuestro objeto app. También podemos manejar métodos HTTP como GET, POST, PUT/PATCH, y DELETE.

Está es la forma más simple de definir rutas, pero a medida que nuestra aplicación crezca, necesitaremos más organización para nuestras rutas. Tan solo imagínate una app que tenga una parte de administrador y otra parte para el usuario, con muchas rutas cada una. Express router nos ayuda a regular todo esto.

Para las rutas siguientes, no enviaremos vistas al navegador, solo mensajes. Así será más sencillo ya que quiero centrarme en los aspectos del routing.

EXPRESS.ROUTER()

express.Router() actúa como una mini aplicación. Puedes crear una instancia (como hicimos con Express) y luego definir rutas con ella. Vamos a ver un ejemplo.

Debajo nuestro app.get() route dentro del server.js, añade lo siguiente. Vamos a 1. llamar una instancia del router 2. aplicarle rutas a esa instancia 3. y luego añadir estas rutas a nuestra app principal.
