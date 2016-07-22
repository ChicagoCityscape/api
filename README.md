# Chicago Cityscape API

The Chicago Cityscape API returns data about an address or PIN in Cook County, Illinois. Returned data includes zoning districts for Chicago properties, ward, community area, state legislative districts, school attendance boundaries, and nearby train station entrances. 

## Endpoint

````
https://www.chicagocityscape.com/tod/index.php
````

We have another endpoint: [Boundaries (Places)](https://github.com/ChicagoCityscape/api/blob/master/boundaries.md) to get GeoJSON for wards, community areas, neighborhoods, Chicago Public Schools attendance areas, and more. 

## Sample request

Fetch a response by using this query on the API:
````
https://www.chicagocityscape.com/tod/index.php?address=333 N Michigan Ave&city=Chicago&state=IL
````

## Parameters

The parameters you must provide are grouped. Only one group of parameter(s) is necessary. 

### Group 1 - PIN
Send a Cook County `pin` (14 digits, and it may begin with `0`) and the API will try to locate it in the parcels database. If this parameter is provided, all other parameters will be ignored. 

### Group 2 - Full address string
Use `query` and a full address (like `121 N La Salle St, Chicago, IL`) and the API will geocode it. If this parameter is provided, all other parameters will be ignored.

### Group 3 - Address parts 
Provide `address`, `city`, and `state` parameters. `zipcode` is optional. If `city` is empty or not provided, the API will assume `Chicago`. If `state` is empty or not provided, the API will assume `IL` (Illinois). 

### Group 4 - Coordinate
`lat` (latitude) and `lng` (longitude), in the EPSG 4326 (WGS84) projection. This coordinate will be reverse geocoded. 

## Notes

* A parcel that appears in the ````parcels_other```` property may also appear in the ````parcels_intersecting```` property if its attribute ````intersects```` is ````1````.
* Responses are cached for one hour.

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
