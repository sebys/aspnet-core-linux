Contenido sobre la presentación ASP.NET CORE en Linux.

## Slides
- [Título](#titulo)
- [.NET Framework](#.net-framework) 
- [.NET Core](#.net-core)
- [.NET CLI](#.net-cli) 
- [ASP.NET](#asp.net)
- [Evolución de ASP.NET](#evolucion_de_asp.net)
- [ASP.NET Core](#asp.net_core)
- [Kestrel](#kestrel)

## Titulo

El contenido de esta presentación abarca una introducción a .NET Core y ASP.NET. La demo propuesta consta de la creación y ejecución de aplicaciones ASP.NET Core en Linux - distribución Ubuntu 16.04 -.

## .NET Framework

.NET Framework es una tecnología desarrollado por Microsoft que soporta la compilación y ejecución de aplicaciones en Windows.

Esta compuesto de:

- **Lenguajes y Compiladores para los lenguajes**: no generan codigo nativo, sino código IL (intermediate language).
- **Runtime de ejecución**: interpreta el código IL y lo combierte a código nativo - JIT -. Servicios que nos ofrece: Garbage collector, compilador JIT.
- **Base Class Library**: librería base.

Como funciona: 

![Funcionamiento del framework](https://github.com/sebys/aspnet-core-linux/tree/master/slides/img/netframework.svg)

Cuando compilamos nuestra aplicación, el compilador del lenguaje genera código IL.

Cuando el SO detecta que que lo que se ejecuta es código punto .NET, pone a correr el runtime convirtiendo JIT el código IL en código nativo que es ejecutado por la plataforma.

## .NET Core

.NET Core es una versión modular de .NET Framework diseñada para que sea portátil entre plataformas.

Caracteristicas:

- **Open Source**: compiladores, runtime, BLC. 
- **Multiplataforma**: functiona en Windows, Linux y iOS.
- **Modular**: solo usas lo que necesitas (Nuget).
- **CLI**: command line interface.

Es importante tener en cuenta que el "ejecutable" final esta compuesto por el compilador y el runtime. Esto me permite tener distintas aplicaciones corriendo con distintas versiones de .NET, pero lo más importante es que ya no nesecitamos intarlar el framework en los servidores. Desplegar aplicaciones resulta más sencillo.

Al ser modular, solo uso lo que necesito por lo el resultado es un framework bien pequeño - 11 MB - comparado al monolitico .NET Framework. La gestión de dependencias se hacen por medio de Nuget.

Gracias a CLI podemos crear, ejecutar y deplegar aplicaciones .NET CORE desde la consola - comando `dotnet` -.
 
En Linux solo se tiene soporte en las distribuciones LTS.

Código fuente: https://github.com/dotnet

## .NET CLI

.NET Command Line Interface: herramienta para compilar, desplegar y administrar aplicaciones .NET en todas las plataformas. Desde el comienzo de punto .NET fue sufriendo algunos cambios: dnx ... dotnet.

Comandos de la herramienta de línea de comandos "dotnet":

- **new**
- **restore**
- **run**
- **build**
- **publish**
- **test**
- **pack**

The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.

https://docs.microsoft.com/en-us/dotnet/articles/core/tools/

## ASP.NET

ASP.NET es el framework de MS para la construcción de aplicaciones web.

- **Web**: MVC, Web Forms, Web Pages.
- **APIs**: Web API
- **RealTime**: SignalR

## Evolución de ASP.NET

El framework ASP.NET a sufrido grandes cambios a traves del tiempo, adaptandose a las necesidades de cada momento.

- **ASP**: programación similar a php con vbscript.
- **ASP.NET WebForm**: necesidad de atraer desarrolladores de aplicaciones de escritorio a la plataforma web - surgimiento de la web -. Hace 15 años aproximadamente.
- **ASP.NET MVC**: Integración con los estandares web (Javascript, HTML, etc).
- **ASP.NET CORE**: modular, preparado para el cloud, multi plataforma, desacoplado de Windows y de IIS.

Necesidades de las aplicaciones web son diferentes ahora que hace 10 años atrás, hoy necesitamos estar conectados todo el tiempo. Necesitamos servidores web optimizados para atender gran cantidad de requests con poco ancho de banda y uso de CPU. Nada mejor que servidores UNIX para estos tipos de escenarios.

## ASP.NET Core

Caracteristicas:

- Modular
- Preparado para el cloud
- Open Source
- Editores o herramientas de desarrollo
- Cross Platform

ASP.NET Core is a new open-source and cross-platform framework for building modern cloud based internet connected applications, such as web apps, IoT apps and mobile backends. 

ASP.NET Core has a number of architectural changes that result in a much leaner and modular framework. ASP.NET Core is no longer based on System.Web.dll. It is based on a set of granular and well factored NuGet packages. This allows you to optimize your app to include just the NuGet packages you need. The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.

https://docs.microsoft.com/en-us/aspnet/core/

## ASP.NET Core Caracteristicas

Unifación proceso de creación de aplicaciones web UI y web API.
Integration of modern client-side frameworks and development workflows (gulp, grunt, bower, bootstrap, knockout.js, angular, less, sass, typescript, etc)
A cloud-ready environment-based configuration system
Inyección de dependencias integrado
New light-weight and modular HTTP request pipeline
Ability to host on IIS or self-host in your own process
Built on .NET Core, which supports true side-by-side app versioning
Ships entirely as NuGet packages
New tooling that simplifies modern web development
Construir y ejecutar aplicaciones ASP.NET multiplataforma en Windows, Mac y Linux
Open source y centrado en la comunidad

## ASP.NET Core Devs

Program class:
--------------
Una aplicación ASP.NET Core es una aplicación de consola sencilla que crea un web server en el método "main". Esto es posible gracias al WebHostBuilder que nos permite configurar el web server y la clases de inicialización - startup class -.

The Build and Run methods build the IWebHost object that will host theapp and start it listening for incoming HTTP requests.

Startup:
--------

La clase Startup es donde definimos el "request handling pipeline" y donde se configuran todos los servicios necesarios por la aplicación. La clase Startup debe ser publica y contar con dos métodos: ConfigureServices y Configure.

* ConfigureServices: defines thes ervices used by your app (such as the ASP.NET MVC, Coreframework, Entity Framework Core, Identity, etc.).

* Configure: defines the middleware in the request pipeline.

Services
--------
Los servicios son componentes que van a ser utilizados de forma concurrente por la aplicación (frameworks o servicios). Estos servicios están disponibles por medio de la inyección de dependencias (DI). ASP.NET Core incluye un contenedor de inversión de control (IoC) que por default permite la inyección por constructor.

ASP.NET Core fue diseñado desde cero para soportar y aprovechar la inyección de dependencias por lo que incorpora un contenedor de inversión de control que se configura en la clase Startup, pero el mismo posee de capacidades reducidas y no pretende reemplazar otros contenedores.

Cuando agregamos servicios al contenedor podemos especificarle el ciclo de vida del mismo: transient, scoped, singleton.

Middleware
----------
El request pipeline de ASP.NET Core consiste en una secuencia de delegados de solicitud - request delegate -que son llamados uno después de otro.

En ASP.NET Core nosotros definimos el request pipeline por medio de los Middleware. Cuando una petición llega a una aplicación ASP.NET Core, es procesada por los middlewares que han sido introducidos en el pipeline desde el método Configure() de la clase Startup, y que componen una cadena colaborativa de proceso de peticiones.

Cada middleware puede ejecutar operaciones antes y despues de invocar al siguiente. Además es posible decidir si pasar la solicitud al siguiente delegado o interrunpir esta secuencia - short-circuiting - (por ejemplo el middleware de archivos staticos sirve el file, por lo que es inutil continuar con el resto).

Host and Servers
----------------
Las aplicaciones ASP.NET Core requieren un host en el cual ejecutarse - generalmente una instancia de WebHostBuilder -. En las propiedades del webhost se especifica el server que manejara los request.

ASP.NET Core incluye un servidor web multi-plataforma administrado llamado Kestrel que normalmente se ejecuta detrás de un servidor web de producción como IIS o nginx.

UseKestrel creates the web server and hosts the code. 
UseIISIntegration specifies IIS as the reverse proxy server.

El host es responsable por la puesta en marcha de la aplicación y la gestión de su ciclo de vida. El server es response por aceptar los HTTP Request. El host está configurado para usar un determinado server, pero el server no tiene conocimiento del host.

Cuando arrancamos el host "run" ponemos a andar el servidor.

Content root
------------
Es el directorio donde se encuentra el contenido de la aplicación, como por ejemplo los archivos de las vistas MVC. Por defecto es la misma carpeta donde corre la aplicación.

Web root
--------
Es el directorio de nuestra aplicación donde se encuentra el contenido público como por ejemplo recursos estáticos como archivos css, js o imagenes. 

Configuration
-------------
ASP.NET Core usa un nuevo modelo de configuración basado en los pares nombre-valor. Este nuevo modelo no está basado en System.Configuration y el web.config, sino que extrae la información de un conjunto ordenado de proveedores de configuración. Los proveedores de configuración incorporados soportan una gran cantidad de formatos  de archivo (XML, JSON, INI) y variables de entorno (con información especifica a cada uno).

En el constructor de la clase Startup leemos los valores de configuración desde un proveedor de configuración JSON que tiene dos variantes, configuración general y por diferentes entornos:

 var builder = new ConfigurationBuilder()
                .SetBasePath(env.ContentRootPath)
                .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
                .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                .AddEnvironmentVariables();
           
Environments
------------
ASP.NET Core introduces improved support for controlling application behavior across multiple environments,
such as development, staging and production. Environment variables are used to indicate which environment
the application is running in allowing th eapp to be configured appropriately.

ASP.NET Corereferences a particular environmentvariable, ASPNETCORE_ENVIRONMENT to describetheenvironment
theapplication is currently running in.This variablecan beset to any valueyou like, but three values are used by
convention: Development , Staging ,and Production . You will find these values used in the samples and
templates provided with ASP.NET Core. 

By default:
Launch.json > configurations > env > ASPNETCORE_ENVIRONMENT

Otra opción:
new WebHostBuilder().UseEnvironment("Development")


## KESTREL

Las aplicaciones ASP.NET Core corren sobre una implementación de HTTP Server. Esta implementación de server escucha las solicitudes HTTP y las transfiere a la aplicación por medio de una instancia HTTPContext.

Las implementaciones de web server disponibles son:
- Kestrel
- WebListener (Only Windows)

Kestrek es un servidor de aplicaciones ASP.NET Core multi-plataforma, asincronico, basado en Libuv (librería I/O asyc cross-platform). Es el web server que ASP.NET Core incluye por default cuando creamos un nuevo proyecto.

No está pensado para extar expuesto hacia afuera, solamente de procesar request. Por lo tanto sobre Kestrel deberíamos montar un reverse proxy server que cuente con carácteristicas como: virtual host, seguridad, loging, cache, etc.

The most important reason for using a reverse proxy for edge deployments (exposed to traffic from the Internet) is security. Kestrel is relatively new and does not yet have a full complement of defenses against attacks.

## ASP.NET Core en Linux

Instalar la última versión de .NET Core: https://www.microsoft.com/net/core#linuxubuntu

Instalar Visual Studio Code con la extensión C#.

Crear directorio "demo" y correr el comando "dotnet new mvc" para crear un proyecto web asp.net core mvc.

En Visual Studio Core abrir la carpeta donde creamos el proyecto.

Abrir el archivo Startup.cs: Visual Studio Core nos pedira restaurar las dependencias del proyecto (1) y agregar los archivos de configuración de compilación y depuración (2).

(1) Una alternativa para restaurar los paquetes es por medio del comando "dotnet restore".
(2) En el archivo launch.json configurar la propiedad program de la siguiente manera:

 "program": "${workspaceRoot}/bin/Debug/netcoreapp1.1/{project_name}.dll",

Copiar el archivo .gitignore usado en las demos.

Realizar modificaciones sobre el código (ver si no mostramos algo de middleware, inyección de dependencias, tag helpers, etc).

Ejecutar y debugear.

Mostrar como podemos ejecutar la aplicación por consola usando el comando "dotnet run".

Integración con Git:
- Clonar repo en el directorio.
- git init
- git remote add origin https://*.git

Pushear cambios, bajar en Windows y ejecutarlo nuevamente.

Publicarlo en Azure y en Linux!