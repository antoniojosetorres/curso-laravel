# Rutas con Laravel
El **sistema de Rutas de Laravel** es bastante intuitivo y fácil de manejar, pero a la vez muy potente, con éste podemos crear todo tipo de rutas en la aplicación: sencillas o complejas.

Las rutas son una capa muy importante en Laravel, es por ello que el framework destina un directorio en la carpeta raíz, llamado `routes`, para ubicar todas las rutas de la aplicación. Por defecto, tiene 2 archivos de rutas `web.php` y `api.php`. Como sus nombres lo expresan en `web.php` se definen las rutas para la web y en `api.php` las rutas para crear APIs para la aplicación.

Podemos definir rutas de varias maneras. En esta lección lo hicimos usando una función anónima, que sigue el siguiente formato:
````php
Route::get('/esta-es-la-url', function () {
    return 'Hola mundo';
});
````
Se escribe la clase `Route` que llama al método relacionado con el verbo HTTP, en este caso, `get` que acepta dos parámetros: el primero es la URL que se llamará desde el navegador y el segundo es una función anónima que devuelve lo que queremos mostrar.

Para ver la ruta en funcionamiento debemos escribir en el navegador algo como: `http://localhost/nombre-proyecto/esta-es-la-url`.

## Rutas con parámetros
También con el sistema de rutas de Laravel puedes crear rutas más complejas que necesiten de parámetros dinámicos. Se pueden definir de la siguiente forma:
````php
Route::get('/usuarios/detalles/{id}', function ($id) {
    return "Detalles del usuario: {$id}";
});
````
En este caso Laravel se encarga de capturar el segmento de la ruta que es dinámico (lo identifica porque está encerrado entre llaves). Por tanto, en la URL pasamos la identificación del parámetro encerrado entre llaves y en la función anónima lo pasamos como argumento para que pueda ser accedido y usado dentro de dicha función.

Se pueden usar tantos parámetros como sean necesarios, solo es importante que estén encerrados entre llaves `{}` y los nombres pueden ser alfanuméricos pero no está permitido usar el guión `-` pero sí el subrayado `_`. Además, importa el orden de los parámetros pasados a la función anónima, pero no los nombres que se les dé. Por ejemplo:
````php
Route::get('posts/{post_id}/comments/{comment_id}', function ($postId, $commentId) {
    return "Este el comentario {$commentId} del post {$postId}";
});
````

## Rutas con filtros o restricciones de expresiones regulares en los parámetros
Cuando un usuario hace una petición HTTP, Laravel busca en los archivos de rutas una definición que coincida con el patrón de la URL según el método HTTP usado y en la primera coincidencia le muestra el resultado al usuario. **Por tanto el orden de precedencia de las definiciones de rutas es muy importante**.

Para solucionar los posibles conflictos con el parecido en la URL de distintas rutas puedes hacerlo de 2 maneras:
* Usando el método `where` para agregar condiciones de expresiones regulares a la ruta.
* Ordenando las rutas de tal manera que las más específicas estén al principio y las más generales al final del archivo de rutas.

## Rutas con parámetros opcionales
Cuando el uso de un parámetro no es obligatorio, podemos usar el carácter `?` después del nombre del parámetro para indicar que es opcional. Sin embargo, debe añadirse un valor por defecto al parámetro cuando lo colocamos en la función, por ejemplo:
````php
Route::get('saludo/{name}/{nickname?}', function ($name, $nickname = null) {
    if ($nickname) {
        return "Bienvenido {$name}, tu apodo es {$nickname}";
    } else {
        return "Bienvenido {$name}, no tienes apodo";
    }
});
````
