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
```

or

```cmd
dotnet tool install --global dotnet-dump --version 3.*
dotnet tool install --global dotnet-ef --version 3.*
dotnet tool install --global dotnet-gcdump --version 3.*
dotnet tool install --global dotnet-trace --version 3.*
dotnet tool install --global dotnet-counters --version 3.*
dotnet tool install --global dotnet-symbol --version 3.*
```

or

```cmd
dotnet tool update --global dotnet-dump  
dotnet tool update --global dotnet-ef  
dotnet tool update --global dotnet-gcdump  
dotnet tool update --global dotnet-trace  
dotnet tool update --global dotnet-counters  
dotnet tool update --global dotnet-symbol
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

dotnet tool uninstall --global dotnet-dump
dotnet tool uninstall --global dotnet-ef
dotnet tool uninstall --global dotnet-gcdump 
dotnet tool uninstall --global dotnet-trace
dotnet tool uninstall --global dotnet-counters
dotnet tool uninstall --global dotnet-symbol

dotnet tool update --global dotnet-dump  --configfile %nugetFile%
dotnet tool update --global dotnet-ef  --configfile %nugetFile%
dotnet tool update --global dotnet-gcdump  --configfile %nugetFile%
dotnet tool update --global dotnet-trace  --configfile %nugetFile%
dotnet tool update --global dotnet-counters  --configfile %nugetFile%
dotnet tool update --global dotnet-symbol  --configfile %nugetFile%

dotnet tool list --global
```

### Performance Diagnosing

- `dotnet counters`
- `dotnet trace`
- `dotnet dump`
- `dotnet monitor`

## AutoMapper

>Alternatives: Pure functions (faster, less hassle)

- <https://cezarypiatek.github.io/post/why-i-dont-use-automapper/>
- <https://ivanazure.wordpress.com/2015/12/02/why-automapping-is-bad-for-you/>

## Information

- Nuget: <https://github.com/boeschenstein/nuget>
