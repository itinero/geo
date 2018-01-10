# geo

[![Build status](http://build.itinero.tech:8080/app/rest/builds/buildType:(id:Itinero_Geo)/statusIcon)](https://build.itinero.tech/viewType.html?buildTypeId=Itinero_Geo)
[![Join the chat at https://gitter.im/Itinero/Lobby](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/Itinero/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Visit our website](https://img.shields.io/badge/website-itinero.tech-020031.svg) ](http://www.itinero.tech/)
[![Apache 2.0 licensed](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/itinero/geo/blob/master/LICENSE.md)

A module to use Itinero together with NTS and IO from common geo formats. The following projects can be found in this repo:

- Itinero.Geo: Links Itinero and NTS together. [![NuGet Badge](https://buildstats.info/nuget/Itinero.Geo)](https://www.nuget.org/packages/Itinero.Geo/)
- Itinero.IO.Shape: IO to read/write routable shapefiles. [![NuGet Badge](https://buildstats.info/nuget/Itinero.IO.Shape)](https://www.nuget.org/packages/Itinero.IO.Shape/)

## How to use

The biggest usecase is to load shapefiles into Itinero:

```csharp

// the vehicle profile defines the from and to columns and things like speeds per link type.
var vehicle = DynamicVehicle.LoadFromStream(File.OpenRead("car.lua")); // load data for the car profile.

// create a new router db and load the shapefile.
var routerDb = new RouterDb(EdgeDataSerializer.MAX_DISTANCE);
routerDb.LoadFromShape("/path/to/shape/", "wegvakken.shp", vehicle);

// write the router db to disk for later use.
routerDb.Serialize(File.OpenWrite("nwb.routerdb"));
```

More info is in the sample in this repo.


