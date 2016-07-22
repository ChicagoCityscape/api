# Chicago Cityscape API

The Chicago Cityscape API returns data about an address or PIN in Cook County, Illinois. Returned data includes zoning districts for Chicago properties, ward, community area, state legislative districts, school attendance boundaries, and nearby train station entrances. 

## Endpoint

````
http://tod.chicagocityscape.com/tod/index.php?[parameter=]
````

## Sample request

Fetch a response by using this query on the API:
````
http://tod.chicagocityscape.com/tod/index.php?address=333 N Michigan Ave&city=Chicago&state=IL
````

## Parameters

Parameters to find the address or PIN are grouped. 

### Group 4 - Coordinate
`lat` (latitude) and `lng` (longitude), in the EPSG 4326 (WGS84) projection. This coordinate will be reverse geocoded. 

### Group 2 - Full address string
Use `query` and a full address (like `121 N La Salle St, Chicago, IL`) and the API will geocode it. 

### Group 1 - PIN
Send a Cook County `pin` (14 digits, and it may begin with `0`) and the API will try to locate it in the parcels database. If this parameter is provided, all other parameters will be ignored. 

### Group 3 - Address parts 
Provide `address`, `city`, and `state` parameters. `zipcode` is optional. If `city` is empty or not provided, the API will assume `Chicago`. If `state` is empty or not provided, the API will assume `IL` (Illinois). 

## Notes

* A parcel that appears in the ````parcels_other```` property may also appear in the ````parcels_intersecting```` property if its attribute ````intersects```` is ````1````.

## Sample response
This will return valid GeoJSON, with a single geometry representing the location of the requested address, or the centroid of the requested PIN:

````
{
    "type": "Feature",
    "geometry": {
        "type": "Point",
        "coordinates": [
            -87.629688,
            41.879666
        ]
    },
    "properties": {
        "request": {
            "address": "56 W Adams St",
            "city": "Chicago",
            "state": "Illinois",
            "reverse_geocoded": true,
            "lat": "41.879666",
            "lng": "-87.629688"
        },
        "parcels_intersecting": [
            {
                "requested_address": "56 W Adams St",
                "pin": "17162120150000",
                "address": "140 S DEARBORN ST",
                "distance_to_centroid": "49.71",
                "distance_to_edge": "0.00",
                "intersects": "1",
                "area": "23908",
                "lng": "-87.629717",
                "lat": "41.879800",
                "class": "5-91",
                "description": "Commercial building over three stories"
            }
        ],
        "parcels_other": null,
        "aro": {
            "geoid": "17031839100",
            "category": "downtown"
        },
        "zoning": {
            "class": "DC-16"
        },
        "pedestrian_street": [],
        "boundaries": [
            {
                "type": "ward",
                "id": "42",
                "name": "42",
                "metadata": "BRENDAN REILLY"
            },
            {
                "type": "communityarea",
                "id": "38",
                "name": "LOOP",
                "metadata": "32"
            },
            {
                "type": "neighborhood",
                "id": "8",
                "name": "The Loop",
                "metadata": null
            },
            {
                "type": "nationalregister",
                "id": "99",
                "name": "Marquette Building",
                "metadata": null
            },
            {
                "type": "tif",
                "id": "79",
                "name": "LaSalle Central",
                "metadata": "Commercial"
            }
        ],
        "mpea": [
            "Lake Michigan Area boundary"
        ],
        "train_stations": {
            "count_entrances": 104,
            "count_stations": 21,
            "search_radius_feet": 2700,
            "entrances": [
                {
                    "gid": "249",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "111.78",
                    "station_id": "790",
                    "manhattan": "154.15",
                    "lat": "41.8799242",
                    "lng": "-87.6294664"
                },
                {
                    "gid": "250",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "154.64",
                    "station_id": "790",
                    "manhattan": "218.69",
                    "lat": "41.8799642",
                    "lng": "-87.629284"
                },
                {"snipped": true}
            ]
        },
        "elapsed_time": 0.5829
    }
}
````

## Creating a subset of parcels

Let's say we don't want to show all parcels on a map, but just the ones represented by a list of PINs (Property Index Numbers). Provided we have the [Cook County parcel shapefile from 2012](https://datacatalog.cookcountyil.gov/GIS-Maps/ccgisdata-Parcel-2012/e62c-6rz8) in our PostGIS database, and a list of PINs, we can easily write a single query that will output the shapes for just our selected PINs.

### Output
If you use just ````psql```` or a GUI PostgreSQL client, then we can return the shapes in a table with one field containing the GeoJSON string for each individual shape. 

To output all of the shapes in a single file (like a shapefile, KML, or GeoJSON file) we'll have to use ````ogr2ogr```` – I prefer this method. 

### Procedures
* First import your list of PINs into a new table in the same database as the Cook County parcel shapefile. 
* Run and test a query like this, changing the table names to match yours: 
````
SELECT * FROM parcel WHERE pin14 in (SELECT pin14 FROM selected_pins)
````
* Now, use these ````ogr2ogr```` command on your local machine (from the working directory where you want the output saved) to output that query's results as different geographic files (KML, GeoJSON, and ESRI Shapefile) using our [ogr2ogr cheat sheet](https://github.com/chicagocityscape/tod-data). 
````
ogr2ogr -f GeoJSON selected_pins.geojson PG:"host=localhost port='5432' dbname='database' user='username' password='password'" -sql "SELECT * FROM parcel WHERE pin14 in (SELECT pin14 FROM selected_pins)" -t_srs "epsg:4326"

ogr2ogr -f KML selected_pins.kml PG:"host=localhost port='5432' dbname='database' user='username' password='password'" -sql "SELECT * FROM parcel WHERE pin14 in (SELECT pin14 FROM selected_pins)" -t_srs "epsg:4326"

ogr2ogr -f "ESRI Shapefile" selected_pins.shp PG:"host=localhost port='5432' dbname='database' user='username' password='password'" -sql "SELECT * FROM parcel WHERE pin14 in (SELECT pin14 FROM selected_pins)" -t_srs "epsg:4326"
````
