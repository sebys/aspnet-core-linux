Contenido sobre la presentación ASP.NET CORE en Linux.

## Slides
- [Título](#titulo)
- [.NET Framework](#.net-framework) 
- [.NET Core](#.net-core) 

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

