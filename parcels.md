# Parcels API
This API returns a GeoJSON dataset of Cook County parcels within a radius (in feet) of a WGS84 geographic coordinate, inside a bounding box passed to the API as a GeoJSON polygon, or inside or within a radius (in feet) of one of our thousands of Place Snapshots (using the `slug` parameter). 
````
/* The endpoint URL...*/
https://www.chicagocityscape.com/api/parcels.php
````

## Details about the Parcels API

### Parameters

The API will return a GeoJSON dataset of Cook County parcels near or within a specific geography. You must provide either a (1) bounding box in GeoJSON, (2) a latitude/longitude coordinate and radius, or (3) a Place Snapshot slug. 

| parameter      | description                                                                                                                                                                                                                              |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| bounds_geojson | Optional. GeoJSON polygon that will be compared against the database of parcels. Must be in the WGS84 coordinate reference system. This was designed to be used with Leaflet, which can generate a bounding box of the current map view. |
| lat            | Optional. Latitude (x) coordinate (required if `lng` is provided)                                                                                                                                                                        |
| lng            | Optional. Longitude (y) coordinate (required if `lat` is provided)                                                                                                                                                                       |
| radius         | Optional. Filter: A number in feet that’s equal to or less than 15,840 feet (3 miles). If `radius` and `slug` are both provided, the API will search for an area beyond the Place Snapshot.                                                      |
| slug           | Optional. Filter: The slug for one of our thousands of Place Snapshots ([find them all](https://www.chicagocityscape.com/maps/index.php)). Example: `communityarea-avondale`. Can be used in combination with `radius`.													|
| include_taxes  | Optional. Set this to `true` to return tax history and tax bill recipient information (this drastically increases the size of the response).                                                                                             |
| chicago_owned  | Optional. Returns information about the potential City-owned land status of each parcel in the response. 
| prop_class     | Optional. Filter: Returns only parcels with the given property class. [Review all the possible property classes](https://www.chicagocityscape.com/guides/propertyclasses.php), used by the Cook County Assessor.
| zone_class     | Optional. Filter: Returns only parcels in a given comma-separated list of Chicago zoning districts.

## Sample API calls

````
/* Get a GeoJSON string of all parcels within 660 feet (1/8th mile) of the given coordinate */
https://www.chicagocityscape.com/api/parcels.php?lat=41.887214&lng=-87.642826&radius=660&key=XXX
````

````
/* Get a GeoJSON string of all parcels within 660 feet (1/8th mile) of the given coordinate that are 2-6 unit apartment buildings (which is represented by the property_class of "2-11") */
https://www.chicagocityscape.com/api/parcels.php?lat=41.887214&lng=-87.642826&prop_class=2-11&radius=660&key=XXX
````

````
/* Get a GeoJSON string of all parcels inside the Logan Square community area */
https://www.chicagocityscape.com/api/parcels.php?slug=communityarea-logan-square&key=XXX
````

````
/* Get a GeoJSON string of all parcels inside the 60606 ZIP code that are in a C1 zoning district */
https://www.chicagocityscape.com/api/parcels.php?slug=zip-60608&zone_class=C1-1,C1-1.5,C1-2,C1-3,C1-5&key=XXX
````

### Sample response

Visualize this GeoJSON on http://geojson.io

````
{
  "count": 4,
  "count_final": 4,
  "note": "Searched for parcels within 50 feet radius/buffer",
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "MultiPolygon",
        "coordinates": [
          [
            [
              [
                -87.64329,
                41.88692
              ],
              [
                -87.64351,
                41.88692
              ],
              [
                -87.64352,
                41.88738
              ],
              [
                -87.64297,
                41.88738
              ],
              [
                -87.64296,
                41.88692
              ],
              [
                -87.64329,
                41.88692
              ]
            ]
          ]
        ]
      },
      "properties": {
        "pin14": "17093090020000",
        "address": "600 W FULTON ST",
        "property_class": {
          "class": "5-91",
          "description": "Commercial building over three stories"
        },
        "city": "CHICAGO",
        "zip_code": "60661",
        "mailing_address": {
          "city_state_zip": "CHICAGO, IL 60661",
          "address": "[hidden]",
          "name": "[hidden]",
          "year": 2013
        },
        "area": 25296,
        "tax_history": [
          "hidden"
        ],
        "acres": 0.5807849646
      }
    },
    {
      "type": "Feature",
      "geometry": {
        "type": "MultiPolygon",
        "coordinates": [
          [
            [
              [
                -87.64193,
                41.88732
              ],
              [
                -87.6415,
                41.88732
              ],
              [
                -87.6415,
                41.8872
              ],
              [
                -87.64205,
                41.88719
              ],
              [
                -87.64205,
                41.88692
              ],
              [
                -87.64211,
                41.88692
              ],
              [
                -87.64211,
                41.88719
              ],
              [
                -87.64267,
                41.88719
              ],
              [
                -87.64267,
                41.88721
              ],
              [
                -87.6424,
                41.88721
              ],
              [
                -87.64241,
                41.88747
              ],
              [
                -87.64268,
                41.88747
              ],
              [
                -87.64268,
                41.88749
              ],
              [
                -87.64241,
                41.88749
              ],
              [
                -87.64265,
                41.88765
              ],
              [
                -87.64269,
                41.88765
              ],
              [
                -87.64269,
                41.88767
              ],
              [
                -87.64213,
                41.88767
              ],
              [
                -87.64214,
                41.88793
              ],
              [
                -87.64209,
                41.88793
              ],
              [
                -87.64208,
                41.88767
              ],
              [
                -87.64151,
                41.88767
              ],
              [
                -87.64151,
                41.88761
              ],
              [
                -87.64235,
                41.88761
              ],
              [
                -87.64234,
                41.88732
              ],
              [
                -87.64193,
                41.88732
              ]
            ]
          ]
        ]
      },
      "properties": {
        "pin14": "17093030820000",
        "address": "310 N CLINTON ST",
        "property_class": {
          "class": "2-90",
          "description": "Minor improvement"
        },
        "city": "CHICAGO",
        "zip_code": "60661",
        "mailing_address": {
          "city_state_zip": "CHICAGO, IL 60654",
          "address": "[hidden]",
          "name": "[hidden]",
          "year": 2013
        },
        "area": 24453,
        "tax_history": [
          "hidden"
        ],
        "acres": 0.56142988665
      }
    },
    {
      "type": "Feature",
      "geometry": {
        "type": "MultiPolygon",
        "coordinates": [
          [
            [
              [
                -87.64267,
                41.88692
              ],
              [
                -87.64267,
                41.88719
              ],
              [
                -87.64211,
                41.88719
              ],
              [
                -87.64211,
                41.88692
              ],
              [
                -87.64267,
                41.88692
              ]
            ]
          ]
        ]
      },
      "properties": {
        "pin14": "17093030871001",
        "address": "560 W FULTON ST",
        "property_class": {
          "class": "2-99",
          "description": "Residential condominium"
        },
        "city": "CHICAGO",
        "zip_code": "60661",
        "mailing_address": {
          "city_state_zip": "CHICAGO, IL 60661",
          "address": "[hidden]",
          "name": "[hidden]",
          "year": 2013
        },
        "area": 15028,
        "tax_history": [
          "hidden"
        ],
        "acres": 0.345052376197
      }
    },
    {
      "type": "Feature",
      "geometry": {
        "type": "MultiPolygon",
        "coordinates": [
          [
            [
              [
                -87.64267,
                41.88721
              ],
              [
                -87.64268,
                41.88747
              ],
              [
                -87.64241,
                41.88747
              ],
              [
                -87.6424,
                41.88721
              ],
              [
                -87.64267,
                41.88721
              ]
            ]
          ]
        ]
      },
      "properties": {
        "pin14": "17093030890000",
        "address": null,
        "property_class": null,
        "city": null,
        "zip_code": null,
        "mailing_address": null,
        "area": 7113,
        "tax_history": [
          "hidden"
        ],
        "acres": 0.16331506774
      }
    }
  ]
}
````
