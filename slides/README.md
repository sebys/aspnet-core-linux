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

El contenido de esta presentación abarca la creación y ejecución de aplicaciones ASP.NET Core en Linux - distribución Ubuntu 16.04 -. 

## .NET Framework

.NET Framework esta compuesto de:

- **Lenguajes y Compiladores para los lenguajes**: no generan codigo nativo, sino código IL.
- **Runtime de ejecución**: interpreta el código IL y lo combierte a código nativo - JIT -. Servicios que nos ofrece: Garbage collector, compilador JIT.
- **Base Class Library**: librería base.

Como funciona: cuando el SO detecta que que lo que se ejecuta es código punto .NET, pone a correr el runtime y ejecuta el código.

## .NET Core

.NET Core es una versión modular de .NET Framework diseñada para que sea portátil entre plataformas.

Caracteristicas:

- **Open Source**: compiladores, runtime, BLC. 
- **Multiplataforma**: functiona en Windows, Linux y iOS.
- **Modular**: solo usas lo que necesitas (Nuget).
- **CLI**: command line interface.

Es importante tener en cuenta que el "ejecutable" final esta compuesto por el compilador y el runtime. Esto me permite tener distintas aplicaciones corriendo con distintas versiones de .NET, pero lo más importante es que ya no nesecitamos intarlar el framework en los servidores. Desplegar aplicaciones resulta más sencillo.

Al ser modular, solo uso lo que necesito por lo el resultado es un framework bien pequeño - 11 MB - comparado al monolitico .NET Framework. La gestión de dependencias se hacen por medio de Nuget.

Gracias a CLI podemos crear, ejecutar y deplegar aplicaciones .NET CORE desde la consola - comando "dotnet" -.
 
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

## Evolución de ASP.NET

El framework ASP.NET a sufrido grandes cambios a traves del tiempo, adaptandose a las necesidades de cada era.

- **ASP**: programación similar a php con vbscript.
- **ASP.NET WebForm**: necesidad de atraer desarrolladores de aplicaciones de escritorio a la plataforma web - surgimiento de la web -. Hace 15 años aproximadamente.
- **ASP.NET MVC**: Integración con los estandares web (Javascript, HTML, etc).
- **ASP.NET CORE**: modular, preparado para el cloud, multi plataforma, desacoplado de Windows y de IIS.

Necesidades de las aplicaciones web son diferentes ahora que hace 10 años atrás, hoy necesitamos estar conectados todo el tiempo. Necesitamos servidores web optimizados para atender gran cantidad de requests con poco ancho de banda y uso de CPU. Nada mejor que servidores UNIX para estos tipos de escenarios.

## ASP.NET Core

Modular
Preparado para el cloud
Open Source
Editores o herramientas de desarrollo
Cross Platform

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

Pipeline and Middleware
Tag Helpers
Dependency Injection

## KESTREL

Servidor de aplicaciones ASP.NET Core, asincronico, multi plataforma, basado en Libuv. 
No está pensado para extar expuesto hacia afuera, solamente de procesar request. 
Sobre Kestrel deberíamos montar uns server proxy que cuente con carácteristicas como: virtual host, seguridad, loging, cache, etc.

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

Integración con Git:
- Clonar repo en el directorio.
- Git init?

Pushear cambios, bajar en Windows y ejecutarlo nuevamente.

Publicarlo en Azure y en Linux!