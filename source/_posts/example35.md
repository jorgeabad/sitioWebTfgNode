title: Manejo de sesiones
tags: []
categories:
  - Módulo 2
  - Express
date: 2015-11-07 20:51:00

---


Manejo de sesiones.
===================
pandoc -s o.docx --no-wrap --reference-links -t markdown -o example35
**Express-session.**

express-session es un midleware para el manejo de sesiones. Su funcionamiento es sencillo, el servidor asigna una “cookie de sesión” al navegador cliente, el navegador, almacena dicha cookie. Esta cookie tiene, como información principal, un identificador único, (que es la llave para recuperar los datos de sesión almacenados en el servidor) y un hash (que el servidor utilizará para asegurarse de que los datos de la cookie no han sido manipulados), a parte, la cookie almacena otra serie de propiedades u opciones configurables.

Es importante señalar y tener claro que **los datos de sesión no se guardan en la cookie de sesión, que almacena el navegador, esta cookie básicamente solamente almacena el ID de sesión**, **los datos de sesión son almacenados en el servidor**.

El almacenamiento de los datos de sesión en el servidor se hace por defecto en la memoria, “MemoryStore”, por lo que esta opción no está diseñada para un entorno de producción, sino más bien destinado a la depuración y el desarrollo. Para producción habría que usar otras opciones de almacenamiento de sesiones, que son módulos que añaden la funcionalidad de interactuar con el sistema de archivos o con base de datos relacionales y NoSql.

Opciones de la cookie de sesión (**lado cliente, navegador**)

-   ***path***: '/',

-   ***httpOnly***: El valor por defecto es ***true***, con esta etiqueta se le indica al navegador que solo ha de permitir el acceso a esta cookie a través del servidor, mediante http. Cualquier intento de acceder a la cookie mediante un script cliente está estrictamente prohibido.

-   ***secure***: Con valor ***true*** Indica que la cookie de sesión **solamente** se puede establecer a través de una conexión **segura, https**. Con valor ***false,*** permite el establecimiento de la cookie, independientemente de si es, o no es, una conexión segura. Por defecto el valor es ***false***.

-   ***maxAge***: Indica cuando expira la cookie de sesión, es decir, cuando expira la sesión y con ello la capacidad de acceder a los datos guardados en el servidor, que están relacionados con esa sesión. El valor por defecto es ***null***, la sesión caduca cuando se cierra el navegador, pero se puede establecer un tiempo en milisegundos.

Opciones para configurar la sesión

cookie Opciones para la cookie de sesión.

genid: función para generar un identificador de sesión. Por defecto usa una función que utiliza la librería uid2

name: es el nombre que se le da a la cookie de sesión, se otorga en la respuesta que el servidor le da al navegador y es la que leerá el servidor para identificar la sesión cuando el navegador hace la petición. El nombre por defecto es “connect.id”, es recomendable configurarlo con otro nombre por motivos de seguridad, y para separar sesiones en el caso de tener varias aplicaciones en el mismo servidor.

Proxy

Resave

Rolling

saveUninitialized

secret

store

unset

{% codeblock prueba lang:javascript http://underscorejs.org/#compact Underscore.js line_number:false %}
function imprimirCabeceraRequestCookie(req){
    var cookiesNavegador=''

    if (typeof req.headers['cookie'] === 'undefined'){

      cookiesNavegador='No hay cookies pasadas por el navegador';
    }else{
      cookiesNavegador=req.headers['cookie'];
    }

    console.log('\n1-REQUEST, solicitud, cookies pasadas por el navegador =', cookiesNavegador);
  }
{% endcodeblock %}


{% codeblock line_number:false highlight:true %}
function imprimirCabeceraRequestCookie(req){
    var cookiesNavegador=''

    if (typeof req.headers['cookie'] === 'undefined'){

      cookiesNavegador='No hay cookies pasadas por el navegador';
    }else{
      cookiesNavegador=req.headers['cookie'];
    }

    console.log('\n1-REQUEST, solicitud, cookies pasadas por el navegador =', cookiesNavegador);
  }
{% endcodeblock %}
