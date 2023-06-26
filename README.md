# .NET Core 3 / .NET 5

## Compatibility (.NET 5)

https://docs.microsoft.com/en-us/dotnet/core/compatibility/5.0

## Upgrade .NET Core 3 -> .NET 5

Edit csproj, change from:

```xml
<TargetFramework>netcoreapp3.1</TargetFramework>
```

to:

```xml
<TargetFramework>net5.0</TargetFramework>
```

## CLI

### Info

Lists all installed sdk and runtime:

`dotnet --info`

### dotnet Tools

- https://docs.microsoft.com/en-us/dotnet/core/tools/global-tools
- https://www.nuget.org/packages?packagetype=dotnettool

Open Visual Studio's Package Manager Console (where Package Source `https://api.nuget.org/v3/index.json` is configured) and start:

```cmd
dotnet tool install --global dotnet-dump  
dotnet tool install --global dotnet-ef  
dotnet tool install --global dotnet-gcdump  
dotnet tool install --global dotnet-trace  
dotnet tool install --global dotnet-counters  
dotnet tool install --global dotnet-symbol
dotnet tool install --global Microsoft.Web.LibraryManager.Cli
```

- There the shortcut for --global: -g
- You can add specific versions. example --version 3.*

Updates:

```cmd
dotnet tool update -g dotnet-dump  
dotnet tool update -g dotnet-ef  
dotnet tool update -g dotnet-gcdump  
dotnet tool update -g dotnet-trace  
dotnet tool update -g dotnet-counters  
dotnet tool update -g dotnet-symbol
dotnet tool update -g Microsoft.Web.LibraryManager.Cli
```

Using nuget.config

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <activePackageSource>
        <add key="NuGet official package source" value="https://api.nuget.org/v3/index.json" />
    </activePackageSource>
</configuration>
```

tool-update.cmd

```dos
SET nugetFile=.\nuget.config

dotnet tool uninstall -g dotnet-dump
dotnet tool uninstall -g dotnet-ef
dotnet tool uninstall -g dotnet-gcdump 
dotnet tool uninstall -g dotnet-trace
dotnet tool uninstall -g dotnet-counters
dotnet tool uninstall -g dotnet-symbol
dotnet tool uninstall -g Microsoft.Web.LibraryManager.Cli

dotnet tool update -g dotnet-dump  --configfile %nugetFile%
dotnet tool update -g dotnet-ef  --configfile %nugetFile%
dotnet tool update -g dotnet-gcdump  --configfile %nugetFile%
dotnet tool update -g dotnet-trace  --configfile %nugetFile%
dotnet tool update -g dotnet-counters  --configfile %nugetFile%
dotnet tool update -g dotnet-symbol  --configfile %nugetFile%
dotnet tool update -g Microsoft.Web.LibraryManager.Cli  --configfile %nugetFile%

dotnet tool list --global
```

### Performance Diagnosing

- `dotnet counters`
- `dotnet trace`
- `dotnet dump`
- `dotnet monitor`

### Upgrade to .NET 5

install or upgrade project converter

```cmd
dotnet tool install -g try-convert
```

install or upgrade "Upgrade assistant"

```cmd
dotnet tool install -g upgrade-assistant
```

Details: <https://github.com/dotnet/upgrade-assistant>

### Local vs Global installation

In a CI/CD project, it is recommended to install the tools locally.

<https://andrewlock.net/new-in-net-core-3-local-tools/>

## AutoMapper

>Alternatives: Pure functions (faster, less hassle)

- <https://cezarypiatek.github.io/post/why-i-dont-use-automapper/>
- <https://ivanazure.wordpress.com/2015/12/02/why-automapping-is-bad-for-you/>

## LibMan - Client Side Package Manager

1. Install LibMan
2. Right-Click on your project: Add... Client-Side Library

## Information

- Nuget: <https://github.com/boeschenstein/nuget>
- LibMan: <https://docs.microsoft.com/en-us/aspnet/core/client-side/libman/libman-cli>
