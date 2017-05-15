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

## Título

El contenido de esta presentación abarca una introducción a .NET Framework, .NET Core, ASP.NET y ASP.NET Core. La demo propuesta consta de la creación y ejecución de aplicaciones ASP.NET Core en Linux - distribución Ubuntu 16.04 -.

## .NET Framework

.NET Framework es una tecnología desarrollado por Microsoft que soporta la compilación y ejecución de aplicaciones en Windows.

Esta compuesto de:

- **Lenguajes y Compiladores para los lenguajes**: no generan código nativo, sino código IL (intermediate language).
- **Runtime de ejecución**: interpreta el código IL y lo convierte a código nativo que es ejecutado por la plataforma.
- **Base Class Library**: librería base.

Funcionamiento:

![Funcionamiento del framework](https://github.com/sebys/aspnet-core-linux/blob/master/slides/img/netframework.png)

Cuando compilamos nuestra aplicación, el compilador del lenguaje genera código IL.

Cuando el SO detecta que lo que se ejecuta es código punto .NET, pone a correr el runtime convirtiendo *just in time* el código IL en código nativo que es ejecutado por la plataforma. El runtime además de ofrecer el compilador JIT nos provee de otros servicios como el Garbage Collector.

Full .NET Framework incluye todas las APIS y asegura compatibilidad par atrás (generalmente viene con el SO).

## .NET Core

.NET Core es una versión modular de .NET Framework diseñada para que sea portátil entre plataformas.

Características:

- **Open Source**: compiladores, runtime, BLC. 
- **Multiplataforma**: funciona en Windows, Linux y iOS.
- **Modular**: solo usas lo que necesitas (Nuget).
- **CLI**: nos provee de herramientas de línea de comando.

.NET Core es open source, incluyendo el runtime y las librerías que componen el framework. Todo el código fuente está disponible en [GitHub](https://github.com/dotnet).

Tal vez el atractivo más grande es que podemos correr nuestras aplicaciones .NET en cualquier plataforma. Tener en cuenta que en Linux solo se tiene soporte en las distribuciones LTS.

Al ser modular solo uso lo que necesito, por lo el resultado es un framework muy pequeño comparado al monolítico .NET Framework. La gestión de dependencias se hacen por medio del gestor de paquetes Nuget.

Es importante tener en cuenta que el "ejecutable" final esta compuesto por el compilador y el runtime. Esto me permite tener distintas aplicaciones corriendo con distintas versiones de .NET, pero lo más importante es que ya no necesitamos instalar el framework en los servidores. Desplegar aplicaciones resulta más sencillo.

Gracias a CLI podemos crear, ejecutar y desplegar aplicaciones .NET Core desde la consola utilizando el comando `dotnet`.

Posee dos grandes frameworks: ASP.NET CORE y UWP

## .NET CLI

La **.NET Command Line Interface** es herramienta que nos permite compilar, desplegar y administrar aplicaciones .NET Core en todas las plataformas. 

Desde el surgimiento de .NET Core fue sufriendo algunos cambios pasando del comando `dnx` o `dnuv` hasta `dotnet`.

Las opciones disponibles para el comando `dotnet`:

- **new**
- **restore**
- **run**
- **build**
- **publish**
- **test**
- **pack**

CLI nos permite montar herramientas de nivel superior, como entornos de desarrollo integrado (IDEs), editores y build orchestrators.

Más información en la [documentación oficial](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/).

## ASP.NET

ASP.NET es el framework de desarrollo web de Microsoft. Esta herramienta nos permite construir diferentes tipos de soluciones webs (aplicaciones, sites y sevicios) del tipo cliente-servidor.

Las alternativas disponibles son:

- **Web**: MVC, Web Forms, Web Pages.
- **APIs**: Web API
- **RealTime**: SignalR

## Evolución de ASP.NET

El framework ASP.NET a sufrido grandes cambios a traves del tiempo, adaptandose a las necesidades de cada momento:

- **ASP**: programación similar a php con vbscript. Lanzado en el año 1996.
- **ASP.NET WebForm**: en pleno surgimiento de la web, se tuvo la necesidad de atraer desarrolladores de aplicaciones de escritorio a la plataforma web. Lanzado en el año 2002.
- **ASP.NET MVC**: integración con los estandares web (Javascript, HTML, etc). Lanzado en el año 2009.
- **ASP.NET CORE**: modular, preparado para el cloud, multi plataforma, desacoplado de Windows y de IIS.

Las necesidades de las aplicaciones web fueron cambiando a traves de los años, hoy necesitamos estar conectados todo el tiempo pero hace 10 años atrás la necesidad principal era servir documentos. 

Actualmente necesitamos servidores web optimizados para atender gran cantidad de requests con poco ancho de banda y uso de CPU, y nada mejor que servidores UNIX para estos tipos de escenarios. Este fue uno de los motivos por el cual aparece .NET Core.

## ASP.NET Core

ASP.NET Cores es un framework open-source y multi-plataforma para construir modernas aplicaciones basadas en la nube conectadas a internet, como web apps, IoT apps y mobile backends.

Características principales:

- Modular
- Preparado para el cloud
- Open Source
- Editores o herramientas de desarrollo
- Cross Platform

ASP.NET Core tiene una serie de cambios arquitectonicos que resultan en un framework mucho más ligero y modular. 

ASP.NET Core ya no se basa en System.Web.dll (logrando desacoplar ASP.NET de Windows y de IIS). Este se basa en conjunto de paquetes NuGet, lo que nos permite optimizar nuestra aplicación ya que solo incluimos los paquetes que necesitamos.

Una aplicación ASP.NET CORE es un app CORE cualquiera (tiene un clase program con un método main), solo que incluye los paquetes de ASP.NET. Como toda aplicación .NET CORE la misma esta compuesta por el compiladores y runtime lo que nos da soporte de side-by-side app versioning (no se requiere tener instalado nada en el servidor).

Esta preparado para el cloud, por que no hay dependencias del web server lo que nos permite publicar nuestras apps en cualquier lado.

El código fuente de ASP.NET Core está disponible en [GitHub](https://github.com/aspnet/Home/blob/dev/CONTRIBUTING.md).

Podemos escribir nuestras aplicaciones en cualquier editor o herramienta de desarrollo moderna (desde Visual Studio o Visual Studio Code hasta Atom o Notepad++). Con Visual Studio o Code tenemos soporte para debug, cosa que otras tools no soportan.

Al ser cross-platform podemos construir y ejecutar aplicaciones ASP.NET multi-plataforma en Windows, Mac y Linux.

Más información en la [documentación oficial](https://docs.microsoft.com/en-us/aspnet/core/).

## Caracteristicas de ASP.NET Core

- Unifación proceso de creación de aplicaciones web UI y web API.
- Integration of modern client-side frameworks and development workflows (gulp, grunt, bower, bootstrap, knockout.js, angular, less, sass, typescript, etc)
- A cloud-ready environment-based configuration system
- Inyección de dependencias integrado
- New light-weight and modular HTTP request pipeline
- Ability to host on IIS or self-host in your own process
- Built on .NET Core, which supports true side-by-side app versioning
- Ships entirely as NuGet packages
- New tooling that simplifies modern web development
- Open source y centrado en la comunidad

## ASP.NET Core Devs

###### Program class:

Una aplicación ASP.NET Core es una aplicación de consola sencilla que crea un web server en el método "main". Esto es posible gracias al WebHostBuilder que nos permite configurar el web server y la clases de inicialización - startup class -.

The Build and Run methods build the IWebHost object that will host theapp and start it listening for incoming HTTP requests.

###### Startup:

La clase Startup es donde definimos el "request handling pipeline" y donde se configuran todos los servicios necesarios por la aplicación. La clase Startup debe ser publica y contar con dos métodos: ConfigureServices y Configure.

* ConfigureServices: defines thes ervices used by your app (such as the ASP.NET MVC, Coreframework, Entity Framework Core, Identity, etc.).

* Configure: defines the middleware in the request pipeline.

###### Services

Los servicios son componentes que van a ser utilizados de forma concurrente por la aplicación (frameworks o servicios). Estos servicios están disponibles por medio de la inyección de dependencias (DI). ASP.NET Core incluye un contenedor de inversión de control (IoC) que por default permite la inyección por constructor.

ASP.NET Core fue diseñado desde cero para soportar y aprovechar la inyección de dependencias por lo que incorpora un contenedor de inversión de control que se configura en la clase Startup, pero el mismo posee de capacidades reducidas y no pretende reemplazar otros contenedores.

Cuando agregamos servicios al contenedor podemos especificarle el ciclo de vida del mismo: transient, scoped, singleton.

###### Middleware

El request pipeline de ASP.NET Core consiste en una secuencia de delegados de solicitud - request delegate -que son llamados uno después de otro.

En ASP.NET Core nosotros definimos el request pipeline por medio de los Middleware. Cuando una petición llega a una aplicación ASP.NET Core, es procesada por los middlewares que han sido introducidos en el pipeline desde el método Configure() de la clase Startup, y que componen una cadena colaborativa de proceso de peticiones.

Cada middleware puede ejecutar operaciones antes y despues de invocar al siguiente. Además es posible decidir si pasar la solicitud al siguiente delegado o interrunpir esta secuencia - short-circuiting - (por ejemplo el middleware de archivos staticos sirve el file, por lo que es inutil continuar con el resto).

###### Host and Servers

Las aplicaciones ASP.NET Core requieren un host en el cual ejecutarse - generalmente una instancia de WebHostBuilder -. En las propiedades del webhost se especifica el server que manejara los request.

ASP.NET Core incluye un servidor web multi-plataforma administrado llamado Kestrel que normalmente se ejecuta detrás de un servidor web de producción como IIS o nginx.

- UseKestrel creates the web server and hosts the code. 
- UseIISIntegration specifies IIS as the reverse proxy server.

El host es responsable por la puesta en marcha de la aplicación y la gestión de su ciclo de vida. El server es response por aceptar los HTTP Request. El host está configurado para usar un determinado server, pero el server no tiene conocimiento del host.

Cuando arrancamos el host "run" ponemos a andar el servidor.

###### Content root

Es el directorio donde se encuentra el contenido de la aplicación, como por ejemplo los archivos de las vistas MVC. Por defecto es la misma carpeta donde corre la aplicación.

###### Web root

Es el directorio de nuestra aplicación donde se encuentra el contenido público como por ejemplo recursos estáticos como archivos css, js o imagenes. 

###### Configuration

ASP.NET Core usa un nuevo modelo de configuración basado en los pares nombre-valor. Este nuevo modelo no está basado en System.Configuration y el web.config, sino que extrae la información de un conjunto ordenado de proveedores de configuración. Los proveedores de configuración incorporados soportan una gran cantidad de formatos  de archivo (XML, JSON, INI) y variables de entorno (con información especifica a cada uno).

En el constructor de la clase Startup leemos los valores de configuración desde un proveedor de configuración JSON que tiene dos variantes, configuración general y por diferentes entornos:

 var builder = new ConfigurationBuilder()
                .SetBasePath(env.ContentRootPath)
                .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
                .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                .AddEnvironmentVariables();
           
###### Environments

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

## ASP.NET Core en Linux (DEMO)

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
