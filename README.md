# Chicago Cityscape API

In private beta. 

## Notes

* A parcel that appears in the ````parcels_other```` property may also appear in the ````parcels_intersecting```` property if its attribute ````intersects```` is ````1````.
* Addresses work best when provided like ````121 N LaSalle St```` (the API is case-insensitive).

## Sample response

Fetch a response by using this query on the API:
````
?lat=41.887542&lng=-87.624407&address=333 N Michigan Ave&city=Chicago
````

This will return:

````
{
    "type": "Feature",
    "geometry": {
        "type": "Point",
        "coordinates": [
            -87.624407,
            41.887542
        ]
    },
    "properties": {
        "parcels_intersecting": [],
        "parcels_other": [
            {
                "requested_address": "333 N Michigan Ave",
                "pin": "17103010030000",
                "address": "333 N MICHIGAN AVE",
                "distance_to_centroid": "64.44",
                "distance_to_edge": "27.08",
                "intersects": "0",
                "area": "3718.09120002375",
                "lng": "-87.624193",
                "lat": "41.887618",
                "class": "5-91",
                "description": "Commercial building over three stories"
            },
            {
                "requested_address": "333 N Michigan Ave",
                "pin": "17103010010000",
                "address": "333 N MICHIGAN AVE",
                "distance_to_centroid": "138.65",
                "distance_to_edge": "62.71",
                "intersects": "0",
                "area": "8484.41651594312",
                "lng": "-87.624203",
                "lat": "41.887890",
                "class": "5-91",
                "description": "Commercial building over three stories"
            }
        ],
        "request": {
            "address": "333 N Michigan Ave",
            "city": "Chicago",
            "state": "",
            "reverse_geocoded": false,
            "lat": "41.887542",
            "lng": "-87.624407"
        },
        "aro": {
            "geoid": "17031320100",
            "category": "downtown"
        },
        "zoning": {
            "class": "DX-16"
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
                "id": "38",
                "name": "Michigan  Wacker Historic District",
                "metadata": null
            }
        ],
        "train_stations": {
            "count": 43,
            "entrances": [
                {
                    "gid": "696",
                    "name": "Millennium Station",
                    "line": null,
                    "agency": "Metra",
                    "distance": "1048.12",
                    "manhattan": "1124.66",
                    "lat": "41.884676",
                    "lng": "-87.6247309"
                },
                {
                    "gid": "378",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1075.18",
                    "manhattan": "1501.04",
                    "lat": "41.8858352",
                    "lng": "-87.6276277"
                },
                {
                    "gid": "379",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1102.57",
                    "manhattan": "1548.55",
                    "lat": "41.8856874",
                    "lng": "-87.6276062"
                },
                {
                    "gid": "695",
                    "name": "Millennium Station",
                    "line": null,
                    "agency": "Metra",
                    "distance": "1156.67",
                    "manhattan": "1245.85",
                    "lat": "41.8843804",
                    "lng": "-87.6247832"
                },
                {
                    "gid": "47",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1183.14",
                    "manhattan": "1664.04",
                    "lat": "41.8855197",
                    "lng": "-87.6278061"
                },
                {
                    "gid": "376",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1226.84",
                    "manhattan": "1683.29",
                    "lat": "41.8858332",
                    "lng": "-87.6282889"
                },
                {
                    "gid": "48",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1241.77",
                    "manhattan": "1738.41",
                    "lat": "41.8855207",
                    "lng": "-87.6280783"
                },
                {
                    "gid": "377",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1254.29",
                    "manhattan": "1736.31",
                    "lat": "41.8856814",
                    "lng": "-87.6282822"
                },
                {
                    "gid": "694",
                    "name": "Millennium Station",
                    "line": null,
                    "agency": "Metra",
                    "distance": "1267.51",
                    "manhattan": "1317.93",
                    "lat": "41.8840679",
                    "lng": "-87.6246344"
                },
                {
                    "gid": "45",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1302.92",
                    "manhattan": "1842.54",
                    "lat": "41.8850125",
                    "lng": "-87.6277886"
                },
                {
                    "gid": "46",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1356.44",
                    "manhattan": "1917.33",
                    "lat": "41.8850175",
                    "lng": "-87.6280676"
                },
                {
                    "gid": "43",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1561.13",
                    "manhattan": "2175.42",
                    "lat": "41.8840609",
                    "lng": "-87.6277484"
                },
                {
                    "gid": "44",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1608.87",
                    "manhattan": "2256.06",
                    "lat": "41.8840639",
                    "lng": "-87.6280461"
                },
                {
                    "gid": "41",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1661.48",
                    "manhattan": "2295.51",
                    "lat": "41.8837245",
                    "lng": "-87.627743"
                },
                {
                    "gid": "42",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1706.31",
                    "manhattan": "2375.79",
                    "lat": "41.8837245",
                    "lng": "-87.6280354"
                },
                {
                    "gid": "49",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1727.76",
                    "manhattan": "2376.16",
                    "lat": "41.8916038",
                    "lng": "-87.62768"
                },
                {
                    "gid": "381",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1729.45",
                    "manhattan": "2115.77",
                    "lat": "41.8829657",
                    "lng": "-87.6260895"
                },
                {
                    "gid": "380",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1748.08",
                    "manhattan": "2180.58",
                    "lat": "41.8829636",
                    "lng": "-87.6263228"
                },
                {
                    "gid": "57",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1805.11",
                    "manhattan": "2484.87",
                    "lat": "41.8917755",
                    "lng": "-87.627849"
                },
                {
                    "gid": "235",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "1814.56",
                    "manhattan": "2334.99",
                    "lat": "41.8858372",
                    "lng": "-87.630668"
                },
                {
                    "gid": "52",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1829.43",
                    "manhattan": "2559.72",
                    "lat": "41.8915948",
                    "lng": "-87.628372"
                },
                {
                    "gid": "236",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "1831.25",
                    "manhattan": "2388.32",
                    "lat": "41.8856774",
                    "lng": "-87.6306519"
                },
                {
                    "gid": "50",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1861.93",
                    "manhattan": "2585.64",
                    "lat": "41.8917965",
                    "lng": "-87.6281936"
                },
                {
                    "gid": "51",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1863.48",
                    "manhattan": "2596.63",
                    "lat": "41.8917465",
                    "lng": "-87.6283023"
                },
                {
                    "gid": "238",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1931.29",
                    "manhattan": "2730.48",
                    "lat": "41.8837364",
                    "lng": "-87.629343"
                },
                {
                    "gid": "383",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1959.07",
                    "manhattan": "2350.33",
                    "lat": "41.8823146",
                    "lng": "-87.6260868"
                },
                {
                    "gid": "237",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1965.95",
                    "manhattan": "2780.18",
                    "lat": "41.8837904",
                    "lng": "-87.6295951"
                },
                {
                    "gid": "382",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1969.25",
                    "manhattan": "2396.70",
                    "lat": "41.8823187",
                    "lng": "-87.6262611"
                },
                {
                    "gid": "234",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "2011.49",
                    "manhattan": "2540.59",
                    "lat": "41.8858551",
                    "lng": "-87.6314405"
                },
                {
                    "gid": "239",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2096.60",
                    "manhattan": "2963.44",
                    "lat": "41.883375",
                    "lng": "-87.6297158"
                },
                {
                    "gid": "233",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "2107.71",
                    "manhattan": "2691.48",
                    "lat": "41.8856515",
                    "lng": "-87.6317221"
                },
                {
                    "gid": "240",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2219.47",
                    "manhattan": "3107.64",
                    "lat": "41.882703",
                    "lng": "-87.6293564"
                },
                {
                    "gid": "242",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2251.03",
                    "manhattan": "3160.74",
                    "lat": "41.882716",
                    "lng": "-87.6295669"
                },
                {
                    "gid": "243",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2286.39",
                    "manhattan": "3189.84",
                    "lat": "41.8824694",
                    "lng": "-87.6293483"
                },
                {
                    "gid": "241",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2327.88",
                    "manhattan": "3257.47",
                    "lat": "41.8824504",
                    "lng": "-87.6295696"
                },
                {
                    "gid": "38",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2352.72",
                    "manhattan": "3052.43",
                    "lat": "41.8815568",
                    "lng": "-87.6276465"
                },
                {
                    "gid": "37",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2383.79",
                    "manhattan": "3125.23",
                    "lat": "41.8815408",
                    "lng": "-87.6278906"
                },
                {
                    "gid": "40",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2444.32",
                    "manhattan": "3151.72",
                    "lat": "41.8812892",
                    "lng": "-87.6276559"
                },
                {
                    "gid": "39",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2472.10",
                    "manhattan": "3218.62",
                    "lat": "41.8812742",
                    "lng": "-87.6278798"
                },
                {
                    "gid": "244",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2578.69",
                    "manhattan": "3530.49",
                    "lat": "41.8814739",
                    "lng": "-87.6292786"
                },
                {
                    "gid": "245",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2652.23",
                    "manhattan": "3614.17",
                    "lat": "41.8812363",
                    "lng": "-87.6292706"
                },
                {
                    "gid": "246",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2684.54",
                    "manhattan": "3679.73",
                    "lat": "41.8812423",
                    "lng": "-87.6295173"
                },
                {
                    "gid": "133",
                    "name": "Merchandise Mart",
                    "line": "Brown, Purple Lines",
                    "agency": "CTA",
                    "distance": "2686.32",
                    "manhattan": "3058.90",
                    "lat": "41.8887076",
                    "lng": "-87.6341482"
                }
            ]
        },
        "elapsed_time": 1.1477
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