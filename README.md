# dotnet5
dotnet5

## Compatibility

https://docs.microsoft.com/en-us/dotnet/core/compatibility/5.0

## dotnet Tools

- https://docs.microsoft.com/en-us/dotnet/core/tools/global-tools
- https://www.nuget.org/packages?packagetype=dotnettool

Open Visual Studio's Package Manager Console (where Package Source `https://api.nuget.org/v3/index.json` is configured) and start:

```cmd
dotnet tool install --global dotnet-dump  
dotnet tool install --global dotnet-ef  
dotnet tool install --global dotnet-gcdump  
dotnet tool install --global dotnet-trace  
dotnet tool install --global dotnet-counters  
```

or

```cmd
dotnet tool update --global dotnet-dump  
dotnet tool update --global dotnet-ef  
dotnet tool update --global dotnet-gcdump  
dotnet tool update --global dotnet-trace  
dotnet tool update --global dotnet-counters  
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

dotnet tool update --global dotnet-dump  --configfile %nugetFile%
dotnet tool update --global dotnet-ef  --configfile %nugetFile%
dotnet tool update --global dotnet-gcdump  --configfile %nugetFile%
dotnet tool update --global dotnet-trace  --configfile %nugetFile%
dotnet tool update --global dotnet-counters  --configfile %nugetFile%

dotnet tool list --global
```
