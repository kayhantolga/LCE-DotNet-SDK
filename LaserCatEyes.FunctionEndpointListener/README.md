# LaserCatEyes DotNet SDK - currently in BETA program
![.NET](https://github.com/betalgo/LCE-DotNet-SDK/workflows/.NET/badge.svg?branch=master)

[![LaserCatEyes.EndpointListener](https://img.shields.io/nuget/v/LaserCatEyes.EndpointListener?label=nuget.LaserCatEyes.EndpointListener)](https://www.nuget.org/packages/LaserCatEyes.EndpointListener/)

[Laser Cat Eyes] is a network monitoring tool that helps mobile app developers diagnose issues between their apps and backend services.

### Installation & Implementation of EnpointListener
1. LaserCatEyes is available through [Nuget](https://www.nuget.org/packages/LaserCatEyes.FunctionEndpointListener/). 
First, [install NuGet](http://docs.nuget.org/docs/start-here/installing-nuget). Then, install [LaserCatEyes.EndpointListener](https://www.nuget.org/packages/LaserCatEyes.EndpointListener/) from the package manager console:
```
PM> Install-Package LaserCatEyes.FunctionEndpointListener
```

2. In ``Startup`` class ``Configure`` method inject middleware
```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        ...
        if (env.IsDevelopment())//This is a debugging tool, you don't want to run it in production, right!?
        {
           ... 
           //Seriously don't run it in production environment 
           app.UseLaserCatEyesFunctionEndpointListenerMiddleware();           
        }
       ...
    }
```
3. In ``Startup`` class ``ConfigureServices`` method inject add Endpoint Listener

```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        ...
        if (env.IsDevelopment())//This is a debugging tool, you don't want to run it in production, right!?
        {
           ... 
           //Seriously don't run it in production environment 
           services.AddLaserCatEyesFunctionEndpointListener(MY_APP_KEY_FROM_LASER_CAT_EYES_PORTAL);
           //OR (more option will be available soon)
           services.AddLaserCatEyesFunctionEndpointListener(option =>
           {
               option.AppKey = MY_APP_KEY_FROM_LASER_CAT_EYES_PORTAL;
               option.AspCoreEnvironment = "STAGE";
               option.Version = "1.2.3.4";
               option.BuildNumber = "1";
           });               
        }
       ...
    }
```

[Laser-Cat-Eyes web portal]: <https://portal.lasercateyes.com>
[Laser Cat Eyes]: <https://lasercateyes.com>

## Author

<img src="http://www.betalgo.com/img/logo-dark.png" width="10px"> Betalgo, mail@betalgo.com
