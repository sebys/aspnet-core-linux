Contenido sobre la presentación ASP.NET CORE en Linux.

## Slides
- [Introducción](#introducción)
- [.NET Framework](#.net-framework) 
- [.NET Core](#.net-core)
- [.NET CLI](#.net-cli) 
- [ASP.NET](#asp.net)
- [Evolución de ASP.NET](#evolucion_de_asp.net)
- [ASP.NET Core](#asp.net_core)
- [Características de ASP.NET Core](#características_de_asp.net_core)
- [ASP.NET Core por dentro](#asp.net_core_por_dentro)
- [Kestrel](#kestrel)

## Introducción

El contenido de esta presentación abarca una introducción a .NET Framework, .NET Core, ASP.NET y ASP.NET Core. La demo propuesta consta de la creación y ejecución de aplicaciones ASP.NET Core en Linux - distribución Ubuntu 16.04 -.

## .NET Framework

.NET Framework es una tecnología desarrollado por Microsoft que soporta la compilación y ejecución de aplicaciones.

Esta compuesto de:

- **Lenguajes y Compiladores para los lenguajes**: no generan código nativo, sino código IL (intermediate language).
- **Runtime de ejecución**: interpreta el código IL y lo convierte a código nativo que es ejecutado por la plataforma.
- **Base Class Library**: librería base.

Funcionamiento:

![Funcionamiento del framework](https://github.com/sebys/aspnet-core-linux/blob/master/slides/img/net-framework-infrastructure.png)

Cuando compilamos nuestra aplicación, el compilador del lenguaje genera código IL.

Cuando el SO detecta que lo que se ejecuta es código punto .NET, pone a correr el runtime convirtiendo *just in time* el código IL en código nativo que es ejecutado por la plataforma. El runtime además de ofrecer el compilador JIT nos provee de otros servicios como el Garbage Collector.

El ecosistema de .NET en la actualidad:

![Ecosistema de .NET](https://github.com/sebys/aspnet-core-linux/blob/master/slides/img/dotnet.png)

- **Full .NET Framework**: incluye todas las APIS y asegura compatibilidad con todas las librerías y frameworks ya conocidos. Solamente corre en Windows y por lo general viene con el sistema operativo. Pesado y monolitico.

- **.NET Core**: framework pequeño, modular - descargo lo que necesito -, side by side y que corre en Windows, Linux y iOS. Como frameworks de alto nivel tenemos ASP.NET CORE y Universal Windows Platform.

- **Xamarin**: se monta sobre la misma infraestructura en común que los otros y tiene su propia BCL y frameworks para el desarrollo de aplicaciones mobile.

## .NET Core

.NET Core es el nuevo framework *open source* de .NET escrito totalmente desde cero. Incluye un subconjunto de la versión completa de .NET Framework y fue diseñado de forma modular para que sea portátil entre plataformas.

Características:

- **Open Source**: compiladores, runtime, BLC. 
- **Multiplataforma**: funciona en Windows, Linux y iOS.
- **Modular**: solo usas lo que necesitas (Nuget).
- **CLI**: nos provee de herramientas de línea de comando.

.NET Core es open source, incluyendo el runtime y las librerías que componen el framework. Todo el código fuente está disponible en [GitHub](https://github.com/dotnet).

Tal vez el atractivo más grande es que podemos correr nuestras aplicaciones .NET en cualquier plataforma (en Linux solo se tiene soporte en las distribuciones LTS).

Al ser modular solo uso lo que necesito, por lo el resultado es un framework muy pequeño comparado al monolítico .NET Framework. La gestión de dependencias se hacen por medio del gestor de paquetes Nuget. Este esquema no solo nos permite incrementar la performance de nuestras aplicaciones sino que nos permite mayor agilidad en nuestros desarrollos, ya que tenemos la posibilidad de elegir las bibliotecas que realmente vamos a utilizar.

Es importante tener en cuenta que el "ejecutable" final esta compuesto por nuestro código, el compilador y el runtime. Esto me permite tener aplicaciones con distintas versiones de .NET corriendo el misma máquina -*side by side*-, por lo tanto ya no necesitamos instalar el framework en los equipos. De esta forma el despliegue de aplicaciones resulta más sencillo.

Gracias a CLI podemos crear, ejecutar y desplegar aplicaciones .NET Core desde la consola utilizando el comando `dotnet`.

__Importante: las aplicaciones .NET Core puedo compilarlas y ejecutarlas a través de los dierentes sistemas opertativos pero no son compatibles a nivel binario. Hay una versión de la BCL compilada de forma diferente para cada sistema operativo (y por lo tanto hacen diferentes llamdas a las primitivas del sistema operativo).

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

![Evolución de ASP.NET](https://github.com/sebys/aspnet-core-linux/blob/master/slides/img/aspnet-framework-evolution.png)

Los principales hitos de este framework a lo largo de su historia fueron:

- **ACTIVE SERVER PAGES**: programación en vbscript similar a php.
- **ASP.NET WebForm**: en pleno surgimiento de la web, se tuvo la necesidad de atraer desarrolladores de aplicaciones de escritorio a la plataforma web.
- **ASP.NET MVC**: integración con los estandares web (Javascript, HTML, etc).
- **ASP.NET CORE**: modular, preparado para el cloud, multi plataforma, desacoplado del servidor y sistema operativo.

Las necesidades de las aplicaciones web fueron cambiando a traves de los años, hoy hay una necesidad de estar conectados todo el tiempo, sin embargo hace 10 años atrás la necesidad principal era servir documentos. En el medio encontramos el surgimiento de los e-shops, aplicaciones backends, redes sociales, etc.

Actualmente necesitamos servidores web optimizados para atender esta gran cantidad de solicitudes que por lo general requieren poco ancho de banda y uso de CPU y la mejor opción para este tipo de escenarios son los servidores UNIX (uno de los motivos por el cual hoy aparece .NET Core).

## ASP.NET Core

ASP.NET Cores es un framework open-source y multi-plataforma para construir modernas aplicaciones conectadas a internet basadas en la nube, como web apps, IoT apps y mobile backends.

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

## Características de ASP.NET Core

Algunas características son:

- Unifación proceso de creación de aplicaciones web UI y web API.
- Intregación con modernos frameroks client-side y workflows de desarrollo (gulp, grunt, bower, bootstrap, knockout.js, angular, less, sass, typescript, etc).
- Sistema de configuración basado en la nube.
- Inyección de dependencias integrado.
- Nuevo HTTP request pipeline, mucho más ligero y modular.
- Capacidad para alojar en IIS or auto-hostearlo en nuestros propios procesos.
- Construido en .NET Core, soportando escenarios side-by-side.
- Nuevas herramientas que simplifican el desarrollo de aplicaciones web modernas.
- Open source y centrado en la comunidad.

## ASP.NET Core por dentro

###### Program class:

Una aplicación ASP.NET Core es una aplicación de consola sencilla que crea un web server en el método `Main`. Esto es posible gracias a `WebHostBuilder` que nos permite configurar el web server y la clases de inicialización - startup class -.

Los métodos `Build` y `Run` del objeto `IWebHost` hostean la aplicación y comienzan a escuchar peticiones HTTP.

###### Startup:

La clase `Startup` es el lugar donde definimos el *request handling pipeline* y donde se configuran todos los servicios necesarios por la aplicación. La clase `Startup` debe ser publica y contar con dos métodos: `ConfigureServices` y `Configure`.

- `ConfigureServices`: es el lugar donde definimos los servicios/frameworks utilizados por la aplicación (como por ejemplo ASP.NET MVC Core framework, Entity Framework Core, Identity, etc.).

- `Configurev`: es el lugar donde definimos los middleware del request pipeline.

###### Services

Los servicios son componentes que van a ser utilizados de forma concurrente por la aplicación (frameworks o servicios). Estos servicios están disponibles por medio de la inyección de dependencias (DI). ASP.NET Core incluye de serie un contenedor de inversión de control (IoC) que por default permite la inyección por constructor.

ASP.NET Core fue diseñado desde cero para soportar y aprovechar la inyección de dependencias por lo que incorpora un contenedor de inversión de control que se configura en el método `ConfigureServices` la clase `Startup`, pero el mismo posee de capacidades reducidas y no pretende reemplazar otros contenedores.

```
public void ConfigureServices(IServiceCollection services)
{
    // Add configuration service.
    services.AddSingleton<IConfiguration>(Configuration);

    // Add framework service.
    services.AddMvc();
}
```

Cuando agregamos servicios al contenedor podemos especificarle el ciclo de vida del mismo: transient, scoped, singleton.

###### Middleware

El request pipeline de ASP.NET Core consiste en una secuencia de delegados de solicitud - request delegate -que son llamados uno después de otro.

En ASP.NET Core nosotros definimos el request pipeline por medio de los Middleware. Cuando una petición llega a una aplicación ASP.NET Core, es procesada por los middlewares que han sido introducidos en el pipeline desde el método `Configure` de la clase `Startup`, y que componen una cadena colaborativa de proceso de peticiones.

```
public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
{
    // Call first to catch exceptions
    // thrown in the following middleware.
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseBrowserLink();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");
    }

    // Return static files and end pipeline.
    app.UseStaticFiles();

    // Add MVC to the request pipeline.
    app.UseMvc(routes =>
    {
        routes.MapRoute(
            name: "default",
            template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

Cada middleware puede ejecutar operaciones antes y despues de invocar al siguiente. Además es posible decidir si pasamos la solicitud al siguiente delegado o interrunpimos esta secuencia - short-circuiting - (por ejemplo el middleware de archivos staticos sirve el file, por lo que es inutil continuar con el resto).

###### Host and Servers

Las aplicaciones ASP.NET Core requieren un host en el cual ejecutarse - generalmente una instancia de `WebHostBuilder` -. Dentro de la configuración del webhost debemos especificar el server que se encargará de atender los request y cual es la configuración de *puesta en marcha* de la aplicación.

```
var host = new WebHostBuilder()
    .UseKestrel()
    .UseContentRoot(Directory.GetCurrentDirectory())
    .UseIISIntegration()
    .UseStartup<Startup>()
    .Build();

host.Run();
```
Las aplicaciones ASP.NET Core corren sobre una implementación de HTTP Server. Esta implementación de server escucha las solicitudes HTTP y las transfiere a la aplicación por medio de una instancia `HttpContext`.

Las implementaciones de web server disponibles son:

- Kestrel
- WebListener (solo en Windows)

ASP.NET Core incluye por default un servidor web multi-plataforma llamado Kestrel, el cual normalmente se ejecuta detrás de un servidor web de producción como IIS o nginx. 

Las propiedades que permiten configurarlo son:

- `UseKestrel`: crea el web server y hostea el código. 
- `UseIISIntegration`: especificamos IIS como el reverse proxy server.

El host es responsable por la puesta en marcha de la aplicación y la gestión de su ciclo de vida. El server es responsable de atender los HTTP Request y servircelos al host por medio de una instancia de `HttpContext`. 

El host está configurado para usar un determinado server, pero el server no tiene conocimiento del host.

Cuando arrancamos el host por medio del método `run` ponemos a andar el servidor.

###### Content root

Es el directorio donde se encuentra el contenido de la aplicación, como por ejemplo los archivos de las vistas MVC. Por defecto es la misma carpeta donde corre la aplicación.

###### Web root

Es el directorio de nuestra aplicación donde se encuentra el contenido público como por ejemplo recursos estáticos como archivos css, js o imagenes. 

###### Configuration

ASP.NET Core usa un nuevo modelo de configuración basado en pares nombre-valor. Este nuevo modelo no está basado en `System.Configuration` y el `web.config`, sino que extrae la información de un conjunto ordenado de proveedores de configuración. Los proveedores de configuración incorporados soportan una gran cantidad de formatos de archivo (XML, JSON, INI) y variables de entorno (con información especifica a cada uno).

En el constructor de la clase `Startup` por defecto leemos los valores de configuración desde un proveedor de configuración JSON que tiene dos variantes: configuración general y por entornos:

```
 var builder = new ConfigurationBuilder()
                .SetBasePath(env.ContentRootPath)
                .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
                .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                .AddEnvironmentVariables();
```

###### Environments

ASP.NET introduce un mejor soporte para controlar nuestra aplicación a traves de multiples entornos, como desarrollo, staging y producción.Las variables de entorno son usadas para indicar en que ambiente la aplicación esta corriendo permitiendo configurarla correctamente.

La variable de entorno por defecto es `ASPNETCORE_ENVIRONMENT` que describe el ambiente en el que la aplicación se ejecuta. Esta variable puede tener cualquier valor, pero por convensión se utilizan los siguientes tres: `Development`, `Staging` y `Production`.

La configuración de la variable de entorno se encuentra en:
`launch.json > configurations > env > ASPNETCORE_ENVIRONMENT`

Otra opción es definirla dentro de la configuración del webhost builder:
`new WebHostBuilder().UseEnvironment("Development")`

## KESTREL

Kestrek es un servidor de aplicaciones ASP.NET Core multi-plataforma, asincronico, basado en Libuv (librería I/O async cross-platform). 

Es el web server que ASP.NET Core incluye por default cuando creamos un nuevo proyecto.

No está pensado para extar expuesto hacia afuera, solamente para procesar requests. Por lo tanto sobre Kestrel deberíamos montar un reverse proxy server que cuente con carácteristicas como: virtual host, seguridad, login, cache, etc. La razón más importante de usar un servidor proxy (expuestos al tráfico de internet) es la seguridad. Kestrel es relativamente nuevo y aún no cuenta con un conjunto completo de defensas contra ataques.

## ASP.NET Core en Linux (DEMO)

1. Instalar la última versión de .NET Core: https://www.microsoft.com/net/core#linuxubuntu
1. Instalar Visual Studio Code con la extensión C#.
1. Crear directorio `demo` y correr el comando `dotnet new mvc` para crear un proyecto web ASP.NET Core MVC.
1. En Visual Studio Core abrir la carpeta donde creamos el proyecto.
1. Abrir el archivo `Startup.cs`: Visual Studio Core nos pedira restaurar las dependencias del proyecto (1) y agregar los archivos de configuración de compilación y depuración (2).
    1. Una alternativa para restaurar los paquetes es por medio del comando "dotnet restore".
    1. En el archivo launch.json configurar la propiedad `program` de la siguiente manera: `"program": "${workspaceRoot}/bin/Debug/netcoreapp1.1/{project_name}.dll"`
1. Copiar el archivo .gitignore usado en las demos.
1. Realizar modificaciones sobre el código (ver si no mostramos algo de middleware, inyección de dependencias, tag helpers, etc).
1. Ejecutar y debugear.
1. Mostrar como podemos ejecutar la aplicación por consola usando el comando `dotnet run`.
1. Integración con Git:
- git init
- git remote add origin https://*.git
1. Pushear cambios, bajar en Windows y ejecutarlo nuevamente.
1. Publicarlo en Azure y en Linux!
