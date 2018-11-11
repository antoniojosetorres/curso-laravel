# Instalación de Composer y Laravel

Para desarrollar aplicaciones de PHP con Laravel necesitamos primero instalar y configurar un conjunto de herramientas que nos facilitan el trabajo de creación de nuevas aplicaciones. Por un lado, requerimos tener un entorno de desarrollo en nuestro equipo que cumpla con los requerimientos del framework y por otro, es recomendable configurar y conocer las formas de acceder a una aplicación creada en dicho entorno. En esta primera lección te guiaremos para que prepares tu equipo y así empieces a desarrollar con Laravel.

## Preparación del entorno de desarrollo
Para desarrollar con Laravel 5.5 puedes hacerlo desde Windows siempre que tengas un servidor web con PHP 7 o superior.

A esto nosotros le llamamos entorno de desarrollo y existe una gran variedad de ellos, cada uno con un nivel de complejidad distinto al otro, desde el más básico instalando manualmente Apache, PHP, MySQL, etc., así como instalar herramientas como XAMPP, etc., hasta otras más complicadas como *Laravel Homestead*.

Sin embargo, recomendamos en Windows usar *Laragon* para quienes estén iniciando, por su facilidad de instalación y uso.

Por otro lado, Laravel utiliza *Composer* para manejar sus dependencias. ¿Qué significa esto? Pues que el framework Laravel hace uso de una colección de paquetes o componentes propios y de terceros para agregarle funcionalidades a las aplicaciones. Por tanto, necesitamos un gestor de dependencias que se encargue automáticamente de crear proyectos, instalar, actualizar o eliminar componentes y a su vez las dependencias de éstos. Esta herramienta es **Composer**, el manejador de dependencias de PHP.

Para Windows puedes descargar el instalador que *ofrece Composer en su sitio web* que se encargará de instalarlo para que lo puedas usar en cualquier parte del sistema. Si has decidido trabajar con *Laragon* no necesitas realizar esta instalación, puesto que viene incluido por defecto en este entorno de desarrollo.

Puedes confirmar si tienes bien instalado Composer ejecutando en la consola desde cualquier directorio: `composer` y en caso de estar instalado, te mostrará un listado de todos los comandos disponibles.

## Instalación de Laravel
Una vez listo el entorno de desarrollo, **usaremos Composer** para instalar Laravel de esta manera: `composer create-project --prefer-dist laravel/laravel mi-proyecto`.

Lo que significa que estamos creando un nuevo proyecto llamado `mi-proyecto` con el comando `create-project` de Composer a partir del paquete `laravel/laravel`, usando la opción `--prefer-dist` para que Composer descargue los archivos del repositorio de distribución.

**Hay una alternativa** para instalar Laravel y es con **su instalador**, que también es un paquete, por tanto, también usaremos Composer para instalarlo de forma global con el comando `composer global require "laravel/installer"`.

Luego, nos tenemos que asegurar que la variable de entorno PATH del sistema operativo tenga incluido el directorio donde se alojan los paquetes instalados globalmente y así se puedan ejecutar sin ningún problema, para ello debemos agregar su ruta. Para Windows debes modificar la variable de entorno PATH para agregar la ruta `;C:\Users\tu-usuario\AppData\Roaming\Composer\vendor\bin`.

Bien, de esta manera ya tenemos disponible el instalador de Laravel, por tanto, podemos ejecutar desde cualquier directorio: `laravel new nombre-proyecto` y se instalará tal y como se hizo con el comando `composer create-project`.

## Abrir la aplicación creada
Para ver y navegar por la aplicación recién creada podemos ejecutar el comando `php artisan serve`.

Este comando ejecuta la aplicación en un servidor de desarrollo incluido por defecto en Laravel. Por tanto debemos hacer clic en la URL que nos muestra para explorar la aplicación en el navegador. Para detener la ejecución presiona `Ctrl+C`.

Si estás usando el entorno de desarrollo Laragon, esta herramienta crea un virtualhost por defecto por cada proyecto según el nombre de la carpeta. Así para nuestro proyecto creado podemos visitar en el navegador `http://mi-proyecto.dev` y podrás ver la aplicación funcionando.
