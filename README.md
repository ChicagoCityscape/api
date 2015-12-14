# Chicago Cityscape API

In private beta. 

## Notes

* A parcel that appears in the ````parcels_other```` property may also appear in the ````parcels_intersecting```` property if its attribute ````intersects```` is ````1````.

## Sample request

Fetch a response by using this query on the API:
````
?lat=41.887542&lng=-87.624407&address=333 N Michigan Ave&city=Chicago
````

### Fields
* lat. Latitude in 4326 projection (required)
* lng. Longitude in 4326 projection (required)
* address. A fully-formed address in Cook County (optional); preferred syntax is ````121 N LaSalle St```` (the API is case-insensitive)
* city. The name of a city in Cook County (optional but required if address provided)
* state. Only "IL" and "Illinois" work (optional)

If address and city are absent, the system will reverse geocode the coordinates to find an address; the ````reverse_geocoded```` property will be ````true````.

## Sample response
This will return:

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
