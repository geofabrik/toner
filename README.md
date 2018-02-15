# Toner for Osm2pgsql Databases

*This is a fork of the map style "Toner" by Stamen Design. The [original
style](https://github.com/stamen/toner-carto) expected an Imposm database. This
fork contains adaptions to be useable with an PostGIS database which was
imported using Osm2pgsql.*

"Toner" is the name of Stamen's black and white map tiles. It was originally
designed for the Dotspotting project by Geraldine Sarmiento, although many
others have been involved since.

The original Toner was developed as part of Stamen's
[Citytracking](https://github.com/Citytracking) initiative, funded by the
[Knight Foundation](http://www.knightfoundation.org/). The old repository can
be found [here](https://github.com/citytracking/toner), for historical
interest.

![Toner screenshot](raw/master/toner_world.png?raw=true)

## Developing and Deploying

### Prerequisites

* PostgreSQL
* PostGIS
* Node.js
* CartoCSS >= 0.18.0
* GDAL
* Python
* Python bindings for GDAL

Optional dependencies for style development:

* Kosmtik (you can also manually render images using Nik4 after each
  modification if you prefer that approach)

Debian/Ubuntu: `nodejs gdal-bin python-gdal nodejs-carto`


### Toner Itself

* Set up a database. See the guides at
  [switch2osm.org/](https://switch2osm.org/) for further information. This map
  style expects a database named `gis` and accesses using the `peer`
  authentication method (i.e. the user which runs Kosmtik/Nik4/the tile server
  has to have read permissions on the tables of that database.
* Clone this repo
* Run `scripts/get-shapefiles.py` to download many shape files from Natural
  Earth and some from openstreetmapdata.com
* Install Kosmtik (it can be installed outside this directory)
* Start Kosmtik by `KOSMTIK_DIR/index.js serve toner.mml`. You can now browse
  the map 

If you just want to deploy this style, you don't need Kosmtik at all. Just run
`carto -a $(mapnik-config -v) toner.mml > toner.xml` to generate the Mapnik
XML.

## License

See the [LICENSE](LICENSE) file. The fonts have different licenses, see the
files at [fonts/](fonts/).
