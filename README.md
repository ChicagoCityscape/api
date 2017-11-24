# Chicago Cityscape API

The Chicago Cityscape API returns data about an address or PIN in Cook County, Illinois. Returned data includes zoning districts for Chicago properties, ward, community area, state legislative districts, school attendance boundaries, and nearby train station entrances. 

Using the API requires a `key` which is available to all Pro members and can be found on your [Account](http://chicagocityscape.com/account.php) page.

## 3 Endpoints

### TOD API 
This API returns information relevant to determining a Chicago address or property's eligibility for transit-oriented development (also called transit-served location) parking minimum reductions and density bonuses.
````
https://www.chicagocityscape.com/api/index.php
````

### Parcels API
This API returns a GeoJSON dataset of Cook County parcels (2015 tax year) within a radius (in feet) of a WGS84 geographic coordinate, inside a bounding box passed to the API as a GeoJSON polygon, or inside or within a radius (in feet) of one of our 2,800 Places (using the `slug` parameter). 
````
https://www.chicagocityscape.com/api/parcels.php
````

### Boundaries API 
Visit [Boundaries (Places)](https://github.com/ChicagoCityscape/api/blob/master/boundaries.md) for details on how to get GeoJSON for wards, community areas, neighborhoods, Chicago Public Schools attendance areas, and other kinds of boundaries.

## Sample requests

Fetch a response by using this query on the TOD API:
````
https://www.chicagocityscape.com/api/index.php?address=333 N Michigan Ave&city=Chicago&state=IL&key=XXX
````

And on the Parcels API:
````
https://www.chicagocityscape.com/api/parcels.php?lat=41.887214&lng=-87.642826&radius=660&key=XXX
````

## Details about the TOD API

### TOD API Parameters

The parameters you must provide are grouped. Only one group of parameter(s) is necessary, plus a valid `key`. 

#### Group 1 - PIN
Send a Cook County `pin` (14 digits, and it may begin with `0`) and the API will try to locate it in the parcels database. If this parameter is provided, all other parameters will be ignored. 

#### Group 2 - Full address string
Use `query` and a full address (like `121 N La Salle St, Chicago, IL`) and the API will geocode it. If this parameter is provided, all other parameters will be ignored.

#### Group 3 - Address parts 
Provide `address`, `city`, and `state` parameters. `zipcode` is optional. If `city` is empty or not provided, the API will assume `Chicago`. If `state` is empty or not provided, the API will assume `IL` (Illinois). 

#### Group 4 - Coordinate
`lat` (latitude) and `lng` (longitude), in the EPSG 4326 (WGS84) projection. This coordinate will be reverse geocoded. 

### Notes

* A parcel that appears in the ````parcels_other```` property may also appear in the ````parcels_intersecting```` property if its attribute ````intersects```` is ````1````.
* Responses are cached for one hour.

### Sample response
This will return valid GeoJSON, with a single geometry representing the location of the requested address, or the centroid of the requested PIN:

````
{
    "type": "Feature",
    "geometry": {
        "type": "Point",
        "coordinates": [
            -87.624523,
            41.88764
        ]
    },
    "properties": {
        "request": {
            "address": "333 N Michigan Ave",
            "city": "Chicago",
            "state": "IL",
            "reverse_geocoded": false,
            "lat": 0,
            "lng": 0,
            "pin": null
        },
        "parcels_intersecting": [],
        "parcels_other": [
            {
                "requested_address": "333 N Michigan Ave",
                "pin": "17103010030000",
                "address": "333 N MICHIGAN AVE",
                "distance_to_centroid": "90.07",
                "distance_to_edge": "58.08",
                "intersects": "0",
                "area": "3718",
                "lng": "-87.624193",
                "lat": "41.887618",
                "class": "5-91",
                "description": "Commercial building over three stories"
            },
            {
                "requested_address": "333 N Michigan Ave",
                "pin": "17103010010000",
                "address": "333 N MICHIGAN AVE",
                "distance_to_centroid": "126.16",
                "distance_to_edge": "61.53",
                "intersects": "0",
                "area": "8484",
                "lng": "-87.624203",
                "lat": "41.887890",
                "class": "5-91",
                "description": "Commercial building over three stories"
            }
        ],
        "aro": [
            {
                "geoid": "17031320100",
                "category": "downtown"
            }
        ],
        "aro_aug2015": [
            {
                "area_numbe": null,
                "community": "DOWNTOWN",
                "category": "downtown"
            }
        ],
        "zoning": {
            "class": "DX-16"
        },
        "zoning_history": [
            {
                "name": "May 2016",
                "zone": "DX-16"
            },
            {
                "name": "November 2015",
                "zone": "DX-16"
            },
            {
                "name": "June 2015",
                "zone": "DX-16"
            },
            {
                "name": "September 2014",
                "zone": "DX-16"
            },
            {
                "name": "August 2012",
                "zone": "DX-16"
            }
        ],
        "pedestrian_street": null,
        "boundaries": {
            "ward": [
                {
                    "type": "ward",
                    "name": "42",
                    "metadata": "BRENDAN REILLY",
                    "slug": "ward-42"
                }
            ],
            "communityarea": [
                {
                    "type": "communityarea",
                    "name": "LOOP",
                    "metadata": "32",
                    "slug": "communityarea-loop"
                }
            ],
            "neighborhood": [
                {
                    "type": "neighborhood",
                    "name": "The Loop",
                    "metadata": "",
                    "slug": "neighborhood-the-loop"
                }
            ],
            "zip": [
                {
                    "type": "zip",
                    "name": "60601",
                    "metadata": "",
                    "slug": "zip-60601"
                }
            ],
            "nationalregister": [
                {
                    "type": "nationalregister",
                    "name": "Michigan  Wacker Historic District",
                    "metadata": "",
                    "slug": "nationalregister-38"
                }
            ],
            "township": [
                {
                    "type": "township",
                    "name": "South",
                    "metadata": "10",
                    "slug": "township-south-10"
                }
            ],
            "chipolicebeat": [
                {
                    "type": "chipolicebeat",
                    "name": "District 01, Beat 0114",
                    "metadata": "01",
                    "slug": "chipolicebeat-district-01-beat-0114"
                }
            ],
            "chipolicedistrict": [
                {
                    "type": "chipolicedistrict",
                    "name": "District 1 - Central",
                    "metadata": "Robert Klich",
                    "slug": "chipolicedistrict-1"
                }
            ],
            "cookcountydistrict": [
                {
                    "type": "cookcountydistrict",
                    "name": "2",
                    "metadata": "Robert Steele",
                    "slug": "cookcountydistrict-2"
                }
            ],
            "mcpier": [
                {
                    "type": "mcpier",
                    "name": "Lake Michigan Area boundary",
                    "metadata": "",
                    "slug": "mcpier-lake-michigan-area"
                }
            ],
            "illinoishouse": [
                {
                    "type": "illinoishouse",
                    "name": "Kenneth Dunkin (5th)",
                    "metadata": "5",
                    "slug": "illinoishouse-5"
                }
            ],
            "illinoissenate": [
                {
                    "type": "illinoissenate",
                    "name": "Mattie Hunter (3rd)",
                    "metadata": "3",
                    "slug": "illinoissenate-3"
                }
            ],
            "cpsattendance": [
                {
                    "type": "cpsattendance",
                    "name": "Wells Hs (HS)",
                    "metadata": "9, 10, 11, 12",
                    "slug": "cpsattendance-wells-hs-hs"
                },
                {
                    "type": "cpsattendance",
                    "name": "Ogden (ES)",
                    "metadata": "K, 1, 2, 3, 4, 5, 6, 7, 8",
                    "slug": "cpsattendance-ogden-es"
                }
            ]
        },
        "mpea": [
            "Lake Michigan Area boundary"
        ],
        "train_stations": {
            "search_radius_feet": 2700,
            "entrances": [
                {
                    "gid": "378",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1071.12",
                    "station_id": "260",
                    "manhattan": "1504.61",
                    "lat": "41.8858352",
                    "lng": "-87.6276277"
                },
                {
                    "gid": "696",
                    "name": "Millennium Station",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "1081.60",
                    "station_id": "5000",
                    "manhattan": "1128.23",
                    "lat": "41.884676",
                    "lng": "-87.6247309"
                },
                {
                    "gid": "379",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1100.54",
                    "station_id": "260",
                    "manhattan": "1552.12",
                    "lat": "41.8856874",
                    "lng": "-87.6276062"
                },
                {
                    "gid": "47",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1181.63",
                    "station_id": "1660",
                    "manhattan": "1667.61",
                    "lat": "41.8855197",
                    "lng": "-87.6278061"
                },
                {
                    "gid": "695",
                    "name": "Millennium Station",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "1189.94",
                    "station_id": "5000",
                    "manhattan": "1249.42",
                    "lat": "41.8843804",
                    "lng": "-87.6247832"
                },
                {
                    "gid": "376",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1218.65",
                    "station_id": "260",
                    "manhattan": "1686.86",
                    "lat": "41.8858332",
                    "lng": "-87.6282889"
                },
                {
                    "gid": "48",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1238.43",
                    "station_id": "1660",
                    "manhattan": "1741.98",
                    "lat": "41.8855207",
                    "lng": "-87.6280783"
                },
                {
                    "gid": "377",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1247.91",
                    "station_id": "260",
                    "manhattan": "1739.88",
                    "lat": "41.8856814",
                    "lng": "-87.6282822"
                },
                {
                    "gid": "694",
                    "name": "Millennium Station",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "1302.06",
                    "station_id": "5000",
                    "manhattan": "1321.50",
                    "lat": "41.8840679",
                    "lng": "-87.6246344"
                }
            ],
            "method": "point_or_centroid",
            "count_entrances": 45,
            "count_stations": 10
        },
        "elapsed_time": 0.0221
    }
}
````

The API response was updated in fall 2017 to include our financial incentives, described in detail in [this issue](https://github.com/ChicagoCityscape/api/issues/1). On the Address Snapshot these are only shown to Pro members. Financial incentives are:
- Chicago Housing Authority (CHA) opportunity areas
- Neighborhood Opportunity Fund (NOF) investment zones
- Retail Thrive Zones (related to NOF)
- Downtown expansion area
- Micro Market Recovery Program (MMRP)

## Details about the Parcels API

### Parameters

The API will return a GeoJSON dataset of Cook County parcels (2015 tax year) near or within a specific geography. You must provide either a (1) bounding box in GeoJSON, (2) a latitude/longitude coordinate and radius, or (3) a Place slug. 

| parameter      | description                                                                                                                                                                                                                              |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| bounds_geojson | Optional. GeoJSON polygon that will be compared against the database of parcels. Must be in the WGS84 coordinate reference system. This was designed to be used with Leaflet, which can generate a bounding box of the current map view. |
| lat            | Optional. Latitude (x) coordinate (required if `lng` is provided)                                                                                                                                                                        |
| lng            | Optional. Longitude (y) coordinate (required if `lat` is provided)                                                                                                                                                                       |
| radius         | Optional. A number in feet that’s equal to or less than 15,840 feet (3 miles).                                                                                                                                                           |
| slug           | Optional. The slug for one of our 2,800 Places. Example: `communityarea-avondale`. Can be used in combination with `radius`.                                                                                                             |
| include_taxes  | Optional. Set this to `true` to return tax history and tax bill recipient information (this drastically increases the size of the response).                                                                                             |
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
