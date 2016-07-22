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
                },
                {
                    "gid": "45",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1306.73",
                    "station_id": "1660",
                    "manhattan": "1846.11",
                    "lat": "41.8850125",
                    "lng": "-87.6277886"
                },
                {
                    "gid": "46",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1358.29",
                    "station_id": "1660",
                    "manhattan": "1920.90",
                    "lat": "41.8850175",
                    "lng": "-87.6280676"
                },
                {
                    "gid": "43",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1572.42",
                    "station_id": "1660",
                    "manhattan": "2178.98",
                    "lat": "41.8840609",
                    "lng": "-87.6277484"
                },
                {
                    "gid": "44",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1618.22",
                    "station_id": "1660",
                    "manhattan": "2259.63",
                    "lat": "41.8840639",
                    "lng": "-87.6280461"
                },
                {
                    "gid": "41",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1674.74",
                    "station_id": "1660",
                    "manhattan": "2299.08",
                    "lat": "41.8837245",
                    "lng": "-87.627743"
                },
                {
                    "gid": "49",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1680.89",
                    "station_id": "330",
                    "manhattan": "2308.82",
                    "lat": "41.8916038",
                    "lng": "-87.62768"
                },
                {
                    "gid": "42",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1717.77",
                    "station_id": "1660",
                    "manhattan": "2379.36",
                    "lat": "41.8837245",
                    "lng": "-87.6280354"
                },
                {
                    "gid": "381",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1755.97",
                    "station_id": "9980",
                    "manhattan": "2119.34",
                    "lat": "41.8829657",
                    "lng": "-87.6260895"
                },
                {
                    "gid": "57",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1758.21",
                    "station_id": "330",
                    "manhattan": "2417.54",
                    "lat": "41.8917755",
                    "lng": "-87.627849"
                },
                {
                    "gid": "380",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1773.21",
                    "station_id": "9980",
                    "manhattan": "2184.15",
                    "lat": "41.8829636",
                    "lng": "-87.6263228"
                },
                {
                    "gid": "52",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1781.97",
                    "station_id": "330",
                    "manhattan": "2492.38",
                    "lat": "41.8915948",
                    "lng": "-87.628372"
                },
                {
                    "gid": "235",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "1797.66",
                    "station_id": "380",
                    "manhattan": "2338.56",
                    "lat": "41.8858372",
                    "lng": "-87.630668"
                },
                {
                    "gid": "50",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1814.72",
                    "station_id": "330",
                    "manhattan": "2518.31",
                    "lat": "41.8917965",
                    "lng": "-87.6281936"
                },
                {
                    "gid": "236",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "1815.72",
                    "station_id": "380",
                    "manhattan": "2391.89",
                    "lat": "41.8856774",
                    "lng": "-87.6306519"
                },
                {
                    "gid": "51",
                    "name": "Grand",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1816.14",
                    "station_id": "330",
                    "manhattan": "2529.30",
                    "lat": "41.8917465",
                    "lng": "-87.6283023"
                },
                {
                    "gid": "238",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1935.53",
                    "station_id": "370",
                    "manhattan": "2734.05",
                    "lat": "41.8837364",
                    "lng": "-87.629343"
                },
                {
                    "gid": "237",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1968.66",
                    "station_id": "370",
                    "manhattan": "2783.75",
                    "lat": "41.8837904",
                    "lng": "-87.6295951"
                },
                {
                    "gid": "383",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1986.81",
                    "station_id": "9980",
                    "manhattan": "2353.90",
                    "lat": "41.8823146",
                    "lng": "-87.6260868"
                },
                {
                    "gid": "234",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "1992.81",
                    "station_id": "380",
                    "manhattan": "2544.16",
                    "lat": "41.8858551",
                    "lng": "-87.6314405"
                },
                {
                    "gid": "382",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1996.07",
                    "station_id": "9980",
                    "manhattan": "2400.27",
                    "lat": "41.8823187",
                    "lng": "-87.6262611"
                },
                {
                    "gid": "233",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "2089.99",
                    "station_id": "380",
                    "manhattan": "2695.05",
                    "lat": "41.8856515",
                    "lng": "-87.6317221"
                },
                {
                    "gid": "239",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2101.22",
                    "station_id": "370",
                    "manhattan": "2967.01",
                    "lat": "41.883375",
                    "lng": "-87.6297158"
                },
                {
                    "gid": "240",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2229.15",
                    "station_id": "370",
                    "manhattan": "3111.21",
                    "lat": "41.882703",
                    "lng": "-87.6293564"
                },
                {
                    "gid": "242",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2259.71",
                    "station_id": "370",
                    "manhattan": "3164.30",
                    "lat": "41.882716",
                    "lng": "-87.6295669"
                },
                {
                    "gid": "243",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2297.14",
                    "station_id": "370",
                    "manhattan": "3193.41",
                    "lat": "41.8824694",
                    "lng": "-87.6293483"
                },
                {
                    "gid": "241",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2337.74",
                    "station_id": "370",
                    "manhattan": "3261.04",
                    "lat": "41.8824504",
                    "lng": "-87.6295696"
                },
                {
                    "gid": "38",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2374.37",
                    "station_id": "1090",
                    "manhattan": "3056.00",
                    "lat": "41.8815568",
                    "lng": "-87.6276465"
                },
                {
                    "gid": "37",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2404.37",
                    "station_id": "1090",
                    "manhattan": "3128.80",
                    "lat": "41.8815408",
                    "lng": "-87.6278906"
                },
                {
                    "gid": "40",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2466.54",
                    "station_id": "1090",
                    "manhattan": "3155.29",
                    "lat": "41.8812892",
                    "lng": "-87.6276559"
                },
                {
                    "gid": "39",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2493.37",
                    "station_id": "1090",
                    "manhattan": "3222.18",
                    "lat": "41.8812742",
                    "lng": "-87.6278798"
                },
                {
                    "gid": "244",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2593.47",
                    "station_id": "790",
                    "manhattan": "3534.06",
                    "lat": "41.8814739",
                    "lng": "-87.6292786"
                },
                {
                    "gid": "133",
                    "name": "Merchandise Mart",
                    "line": "Brown, Purple Lines",
                    "agency": "CTA",
                    "distance": "2649.65",
                    "station_id": "460",
                    "manhattan": "2991.57",
                    "lat": "41.8887076",
                    "lng": "-87.6341482"
                },
                {
                    "gid": "245",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2667.78",
                    "station_id": "790",
                    "manhattan": "3617.73",
                    "lat": "41.8812363",
                    "lng": "-87.6292706"
                },
                {
                    "gid": "131",
                    "name": "Merchandise Mart",
                    "line": "Brown, Purple Lines",
                    "agency": "CTA",
                    "distance": "2668.53",
                    "station_id": "460",
                    "manhattan": "3265.01",
                    "lat": "41.8895811",
                    "lng": "-87.6339725"
                },
                {
                    "gid": "132",
                    "name": "Merchandise Mart",
                    "line": "Brown, Purple Lines",
                    "agency": "CTA",
                    "distance": "2694.26",
                    "station_id": "460",
                    "manhattan": "3269.00",
                    "lat": "41.8894983",
                    "lng": "-87.6340999"
                },
                {
                    "gid": "246",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "2699.08",
                    "station_id": "790",
                    "manhattan": "3683.30",
                    "lat": "41.8812423",
                    "lng": "-87.6295173"
                }
            ],
            "method": "point_or_centroid",
            "count_entrances": 45,
            "count_stations": 10
        },
        "elapsed_time": 1.0221
    }
}
````
