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
                {
                    "gid": "247",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "207.43",
                    "station_id": "790",
                    "manhattan": "256.64",
                    "lat": "41.8802118",
                    "lng": "-87.6294717"
                },
                {
                    "gid": "248",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "235.03",
                    "station_id": "790",
                    "manhattan": "317.61",
                    "lat": "41.8802338",
                    "lng": "-87.6292786"
                },
                {
                    "gid": "251",
                    "name": "Jackson",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "347.45",
                    "station_id": "70",
                    "manhattan": "403.03",
                    "lat": "41.878726",
                    "lng": "-87.6294744"
                },
                {
                    "gid": "252",
                    "name": "Jackson",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "359.91",
                    "station_id": "70",
                    "manhattan": "466.70",
                    "lat": "41.878744",
                    "lng": "-87.6292142"
                },
                {
                    "gid": "33",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "514.77",
                    "station_id": "1090",
                    "manhattan": "618.14",
                    "lat": "41.8799752",
                    "lng": "-87.6278436"
                },
                {
                    "gid": "36",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "544.31",
                    "station_id": "1090",
                    "manhattan": "718.72",
                    "lat": "41.8802627",
                    "lng": "-87.6278557"
                },
                {
                    "gid": "32",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "561.84",
                    "station_id": "560",
                    "manhattan": "747.69",
                    "lat": "41.8789976",
                    "lng": "-87.6278289"
                },
                {
                    "gid": "246",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "576.29",
                    "station_id": "790",
                    "manhattan": "616.55",
                    "lat": "41.8812423",
                    "lng": "-87.6295173"
                },
                {
                    "gid": "35",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "577.79",
                    "station_id": "1090",
                    "manhattan": "690.46",
                    "lat": "41.8800011",
                    "lng": "-87.6276143"
                },
                {
                    "gid": "245",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "583.41",
                    "station_id": "790",
                    "manhattan": "682.12",
                    "lat": "41.8812363",
                    "lng": "-87.6292706"
                },
                {
                    "gid": "34",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "603.25",
                    "station_id": "1090",
                    "manhattan": "782.08",
                    "lat": "41.8802587",
                    "lng": "-87.6276197"
                },
                {
                    "gid": "31",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "609.66",
                    "station_id": "560",
                    "manhattan": "844.16",
                    "lat": "41.878737",
                    "lng": "-87.6278262"
                },
                {
                    "gid": "30",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "627.32",
                    "station_id": "560",
                    "manhattan": "823.15",
                    "lat": "41.8789776",
                    "lng": "-87.6275767"
                },
                {
                    "gid": "244",
                    "name": "Monroe",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "668.18",
                    "station_id": "790",
                    "manhattan": "765.79",
                    "lat": "41.8814739",
                    "lng": "-87.6292786"
                },
                {
                    "gid": "29",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "670.90",
                    "station_id": "560",
                    "manhattan": "919.27",
                    "lat": "41.878714",
                    "lng": "-87.6275794"
                },
                {
                    "gid": "39",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "765.46",
                    "station_id": "1090",
                    "manhattan": "1077.67",
                    "lat": "41.8812742",
                    "lng": "-87.6278798"
                },
                {
                    "gid": "254",
                    "name": "Jackson",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "777.75",
                    "station_id": "70",
                    "manhattan": "905.38",
                    "lat": "41.8775637",
                    "lng": "-87.6291955"
                },
                {
                    "gid": "253",
                    "name": "Jackson",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "780.74",
                    "station_id": "70",
                    "manhattan": "859.15",
                    "lat": "41.8775338",
                    "lng": "-87.6294073"
                },
                {
                    "gid": "40",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "810.02",
                    "station_id": "1090",
                    "manhattan": "1144.56",
                    "lat": "41.8812892",
                    "lng": "-87.6276559"
                },
                {
                    "gid": "37",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "840.45",
                    "station_id": "1090",
                    "manhattan": "1171.05",
                    "lat": "41.8815408",
                    "lng": "-87.6278906"
                },
                {
                    "gid": "256",
                    "name": "Jackson",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "855.51",
                    "station_id": "70",
                    "manhattan": "986.08",
                    "lat": "41.877348",
                    "lng": "-87.6291901"
                },
                {
                    "gid": "255",
                    "name": "Jackson",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "858.89",
                    "station_id": "70",
                    "manhattan": "944.17",
                    "lat": "41.8773201",
                    "lng": "-87.6293832"
                },
                {
                    "gid": "27",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "865.11",
                    "station_id": "60",
                    "manhattan": "1211.67",
                    "lat": "41.8777594",
                    "lng": "-87.6277953"
                },
                {
                    "gid": "38",
                    "name": "Monroe",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "885.35",
                    "station_id": "1090",
                    "manhattan": "1243.86",
                    "lat": "41.8815568",
                    "lng": "-87.6276465"
                },
                {
                    "gid": "26",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "906.12",
                    "station_id": "560",
                    "manhattan": "1262.30",
                    "lat": "41.8776196",
                    "lng": "-87.627798"
                },
                {
                    "gid": "28",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "913.78",
                    "station_id": "560",
                    "manhattan": "1287.47",
                    "lat": "41.8777335",
                    "lng": "-87.6275499"
                },
                {
                    "gid": "374",
                    "name": "Adams\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "937.66",
                    "station_id": "680",
                    "manhattan": "950.96",
                    "lat": "41.8796816",
                    "lng": "-87.626245"
                },
                {
                    "gid": "24",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "951.43",
                    "station_id": "560",
                    "manhattan": "1317.32",
                    "lat": "41.8774708",
                    "lng": "-87.6277967"
                },
                {
                    "gid": "373",
                    "name": "Adams\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "958.87",
                    "station_id": "680",
                    "manhattan": "1088.04",
                    "lat": "41.8792622",
                    "lng": "-87.6262088"
                },
                {
                    "gid": "371",
                    "name": "Adams\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "976.88",
                    "station_id": "680",
                    "manhattan": "1200.75",
                    "lat": "41.8789347",
                    "lng": "-87.626237"
                },
                {
                    "gid": "25",
                    "name": "Jackson",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "991.90",
                    "station_id": "560",
                    "manhattan": "1387.61",
                    "lat": "41.8774668",
                    "lng": "-87.6275419"
                },
                {
                    "gid": "367",
                    "name": "Harold Washington Library",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "996.10",
                    "station_id": "850",
                    "manhattan": "1047.11",
                    "lat": "41.8769376",
                    "lng": "-87.6299103"
                },
                {
                    "gid": "375",
                    "name": "Adams\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1005.37",
                    "station_id": "680",
                    "manhattan": "1031.01",
                    "lat": "41.8797146",
                    "lng": "-87.6259969"
                },
                {
                    "gid": "241",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1015.17",
                    "station_id": "370",
                    "manhattan": "1038.82",
                    "lat": "41.8824504",
                    "lng": "-87.6295696"
                },
                {
                    "gid": "372",
                    "name": "Adams\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1017.22",
                    "station_id": "680",
                    "manhattan": "1147.82",
                    "lat": "41.8792582",
                    "lng": "-87.6259929"
                },
                {
                    "gid": "243",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1025.77",
                    "station_id": "370",
                    "manhattan": "1106.44",
                    "lat": "41.8824694",
                    "lng": "-87.6293483"
                },
                {
                    "gid": "368",
                    "name": "Harold Washington Library",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1030.58",
                    "station_id": "850",
                    "manhattan": "1116.29",
                    "lat": "41.8768467",
                    "lng": "-87.6293899"
                },
                {
                    "gid": "369",
                    "name": "Harold Washington Library",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1072.95",
                    "station_id": "850",
                    "manhattan": "1432.50",
                    "lat": "41.8770035",
                    "lng": "-87.6280059"
                },
                {
                    "gid": "364",
                    "name": "LaSalle\/Van Buren",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1106.63",
                    "station_id": "160",
                    "manhattan": "1471.96",
                    "lat": "41.8769276",
                    "lng": "-87.6314445"
                },
                {
                    "gid": "240",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1110.39",
                    "station_id": "370",
                    "manhattan": "1188.64",
                    "lat": "41.882703",
                    "lng": "-87.6293564"
                },
                {
                    "gid": "242",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1111.94",
                    "station_id": "370",
                    "manhattan": "1135.55",
                    "lat": "41.882716",
                    "lng": "-87.6295669"
                },
                {
                    "gid": "357",
                    "name": "Quincy",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1115.12",
                    "station_id": "40",
                    "manhattan": "1313.59",
                    "lat": "41.8790855",
                    "lng": "-87.6337083"
                },
                {
                    "gid": "370",
                    "name": "Harold Washington Library",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1120.08",
                    "station_id": "850",
                    "manhattan": "1484.61",
                    "lat": "41.8768607",
                    "lng": "-87.6280072"
                },
                {
                    "gid": "359",
                    "name": "Quincy",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1131.16",
                    "station_id": "40",
                    "manhattan": "1385.74",
                    "lat": "41.8788858",
                    "lng": "-87.6337082"
                },
                {
                    "gid": "365",
                    "name": "LaSalle\/Van Buren",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1136.79",
                    "station_id": "160",
                    "manhattan": "1504.02",
                    "lat": "41.8768338",
                    "lng": "-87.6314378"
                },
                {
                    "gid": "356",
                    "name": "Quincy",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1149.10",
                    "station_id": "40",
                    "manhattan": "1349.63",
                    "lat": "41.8790815",
                    "lng": "-87.6338343"
                },
                {
                    "gid": "358",
                    "name": "Quincy",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1163.48",
                    "station_id": "40",
                    "manhattan": "1420.71",
                    "lat": "41.8788808",
                    "lng": "-87.633829"
                },
                {
                    "gid": "361",
                    "name": "Quincy",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1166.25",
                    "station_id": "40",
                    "manhattan": "1509.47",
                    "lat": "41.8785313",
                    "lng": "-87.6336922"
                },
                {
                    "gid": "360",
                    "name": "Quincy",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1199.41",
                    "station_id": "40",
                    "manhattan": "1544.46",
                    "lat": "41.8785343",
                    "lng": "-87.6338236"
                },
                {
                    "gid": "362",
                    "name": "Quincy",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1205.85",
                    "station_id": "40",
                    "manhattan": "1606.60",
                    "lat": "41.8782707",
                    "lng": "-87.6337029"
                },
                {
                    "gid": "366",
                    "name": "LaSalle\/Van Buren",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1210.21",
                    "station_id": "160",
                    "manhattan": "1644.97",
                    "lat": "41.8767739",
                    "lng": "-87.6318723"
                },
                {
                    "gid": "363",
                    "name": "LaSalle\/Van Buren",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1210.80",
                    "station_id": "160",
                    "manhattan": "1678.01",
                    "lat": "41.8769107",
                    "lng": "-87.6321727"
                },
                {
                    "gid": "355",
                    "name": "Washington\/Wells",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1308.55",
                    "station_id": "730",
                    "manhattan": "1804.24",
                    "lat": "41.8816017",
                    "lng": "-87.6337351"
                },
                {
                    "gid": "382",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1343.65",
                    "station_id": "9980",
                    "manhattan": "1899.58",
                    "lat": "41.8823187",
                    "lng": "-87.6262611"
                },
                {
                    "gid": "239",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1351.62",
                    "station_id": "370",
                    "manhattan": "1370.14",
                    "lat": "41.883375",
                    "lng": "-87.6297158"
                },
                {
                    "gid": "354",
                    "name": "Washington\/Wells",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1351.64",
                    "station_id": "730",
                    "manhattan": "1854.21",
                    "lat": "41.8815987",
                    "lng": "-87.6339242"
                },
                {
                    "gid": "383",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1375.99",
                    "station_id": "9980",
                    "manhattan": "1945.95",
                    "lat": "41.8823146",
                    "lng": "-87.6260868"
                },
                {
                    "gid": "259",
                    "name": "LaSalle",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1477.17",
                    "station_id": "1340",
                    "manhattan": "1813.96",
                    "lat": "41.8757643",
                    "lng": "-87.6311588"
                },
                {
                    "gid": "238",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1486.27",
                    "station_id": "370",
                    "manhattan": "1565.80",
                    "lat": "41.8837364",
                    "lng": "-87.629343"
                },
                {
                    "gid": "258",
                    "name": "LaSalle",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1491.92",
                    "station_id": "1340",
                    "manhattan": "1868.12",
                    "lat": "41.8757673",
                    "lng": "-87.63136"
                },
                {
                    "gid": "451",
                    "name": "Van Buren Street",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "1496.04",
                    "station_id": "5008",
                    "manhattan": "1874.37",
                    "lat": "41.8784085",
                    "lng": "-87.6244587"
                },
                {
                    "gid": "237",
                    "name": "Washington",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1503.19",
                    "station_id": "370",
                    "manhattan": "1516.11",
                    "lat": "41.8837904",
                    "lng": "-87.6295951"
                },
                {
                    "gid": "380",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1511.26",
                    "station_id": "9980",
                    "manhattan": "2115.70",
                    "lat": "41.8829636",
                    "lng": "-87.6263228"
                },
                {
                    "gid": "450",
                    "name": "Van Buren Street",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "1526.60",
                    "station_id": "5008",
                    "manhattan": "1969.05",
                    "lat": "41.8781469",
                    "lng": "-87.624464"
                },
                {
                    "gid": "42",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1545.92",
                    "station_id": "1660",
                    "manhattan": "1920.50",
                    "lat": "41.8837245",
                    "lng": "-87.6280354"
                },
                {
                    "gid": "381",
                    "name": "Washington\/Wabash",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1551.20",
                    "station_id": "9980",
                    "manhattan": "2180.52",
                    "lat": "41.8829657",
                    "lng": "-87.6260895"
                },
                {
                    "gid": "353",
                    "name": "Washington\/Wells",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1555.35",
                    "station_id": "730",
                    "manhattan": "2199.16",
                    "lat": "41.8826481",
                    "lng": "-87.633774"
                },
                {
                    "gid": "41",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1570.95",
                    "station_id": "1660",
                    "manhattan": "2000.77",
                    "lat": "41.8837245",
                    "lng": "-87.627743"
                },
                {
                    "gid": "352",
                    "name": "Washington\/Wells",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1583.17",
                    "station_id": "730",
                    "manhattan": "2236.73",
                    "lat": "41.8826242",
                    "lng": "-87.6339456"
                },
                {
                    "gid": "261",
                    "name": "LaSalle",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1584.00",
                    "station_id": "1340",
                    "manhattan": "1927.02",
                    "lat": "41.8754637",
                    "lng": "-87.6311749"
                },
                {
                    "gid": "351",
                    "name": "Washington\/Wells",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1585.12",
                    "station_id": "730",
                    "manhattan": "2241.70",
                    "lat": "41.8827659",
                    "lng": "-87.6337713"
                },
                {
                    "gid": "260",
                    "name": "LaSalle",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1599.02",
                    "station_id": "1340",
                    "manhattan": "1974.84",
                    "lat": "41.8754547",
                    "lng": "-87.6313372"
                },
                {
                    "gid": "350",
                    "name": "Washington\/Wells",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1618.60",
                    "station_id": "730",
                    "manhattan": "2287.95",
                    "lat": "41.882734",
                    "lng": "-87.6339859"
                },
                {
                    "gid": "693",
                    "name": "LaSalle Street",
                    "line": "Rock Island",
                    "agency": "Metra",
                    "distance": "1644.99",
                    "station_id": "6000",
                    "manhattan": "2108.35",
                    "lat": "41.8754368",
                    "lng": "-87.6317999"
                },
                {
                    "gid": "349",
                    "name": "Washington\/Wells",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1646.18",
                    "station_id": "730",
                    "manhattan": "2326.78",
                    "lat": "41.8829896",
                    "lng": "-87.633782"
                },
                {
                    "gid": "44",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1663.85",
                    "station_id": "1660",
                    "manhattan": "2040.22",
                    "lat": "41.8840639",
                    "lng": "-87.6280461"
                },
                {
                    "gid": "348",
                    "name": "Washington\/Wells",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "1669.72",
                    "station_id": "730",
                    "manhattan": "2361.33",
                    "lat": "41.8829417",
                    "lng": "-87.6339751"
                },
                {
                    "gid": "43",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1686.40",
                    "station_id": "1660",
                    "manhattan": "2120.87",
                    "lat": "41.8840609",
                    "lng": "-87.6277484"
                },
                {
                    "gid": "257",
                    "name": "LaSalle",
                    "line": "Blue Line",
                    "agency": "CTA",
                    "distance": "1748.53",
                    "station_id": "1340",
                    "manhattan": "2343.66",
                    "lat": "41.8753858",
                    "lng": "-87.6325898"
                },
                {
                    "gid": "692",
                    "name": "LaSalle Street",
                    "line": "Rock Island",
                    "agency": "Metra",
                    "distance": "1759.61",
                    "station_id": "6000",
                    "manhattan": "2364.96",
                    "lat": "41.8753768",
                    "lng": "-87.6326555"
                },
                {
                    "gid": "448",
                    "name": "Van Buren Street",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "1849.53",
                    "station_id": "5008",
                    "manhattan": "2542.09",
                    "lat": "41.8769875",
                    "lng": "-87.6239195"
                },
                {
                    "gid": "449",
                    "name": "Van Buren Street",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "1908.93",
                    "station_id": "5008",
                    "manhattan": "2357.47",
                    "lat": "41.8781948",
                    "lng": "-87.6229607"
                },
                {
                    "gid": "46",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "1999.45",
                    "station_id": "1660",
                    "manhattan": "2378.95",
                    "lat": "41.8850175",
                    "lng": "-87.6280676"
                },
                {
                    "gid": "45",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2015.81",
                    "station_id": "1660",
                    "manhattan": "2453.74",
                    "lat": "41.8850125",
                    "lng": "-87.6277886"
                },
                {
                    "gid": "22",
                    "name": "Harrison",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2083.85",
                    "station_id": "1490",
                    "manhattan": "2564.37",
                    "lat": "41.8741426",
                    "lng": "-87.6277068"
                },
                {
                    "gid": "21",
                    "name": "Harrison",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2099.46",
                    "station_id": "1490",
                    "manhattan": "2628.06",
                    "lat": "41.8741506",
                    "lng": "-87.6274601"
                },
                {
                    "gid": "694",
                    "name": "Millennium Station",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "2113.56",
                    "station_id": "5000",
                    "manhattan": "2978.35",
                    "lat": "41.8840679",
                    "lng": "-87.6246344"
                },
                {
                    "gid": "695",
                    "name": "Millennium Station",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "2176.13",
                    "station_id": "5000",
                    "manhattan": "3050.43",
                    "lat": "41.8843804",
                    "lng": "-87.6247832"
                },
                {
                    "gid": "48",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2178.08",
                    "station_id": "1660",
                    "manhattan": "2557.87",
                    "lat": "41.8855207",
                    "lng": "-87.6280783"
                },
                {
                    "gid": "47",
                    "name": "Lake",
                    "line": "Red Line",
                    "agency": "CTA",
                    "distance": "2193.85",
                    "station_id": "1660",
                    "manhattan": "2632.24",
                    "lat": "41.8855197",
                    "lng": "-87.6278061"
                },
                {
                    "gid": "236",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "2206.29",
                    "station_id": "380",
                    "manhattan": "2468.83",
                    "lat": "41.8856774",
                    "lng": "-87.6306519"
                },
                {
                    "gid": "377",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "2225.26",
                    "station_id": "260",
                    "manhattan": "2559.97",
                    "lat": "41.8856814",
                    "lng": "-87.6282822"
                },
                {
                    "gid": "233",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "2250.42",
                    "station_id": "380",
                    "manhattan": "2748.34",
                    "lat": "41.8856515",
                    "lng": "-87.6317221"
                },
                {
                    "gid": "235",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "2264.63",
                    "station_id": "380",
                    "manhattan": "2531.88",
                    "lat": "41.8858372",
                    "lng": "-87.630668"
                },
                {
                    "gid": "379",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "2266.32",
                    "station_id": "260",
                    "manhattan": "2747.73",
                    "lat": "41.8856874",
                    "lng": "-87.6276062"
                },
                {
                    "gid": "696",
                    "name": "Millennium Station",
                    "line": "Electric, South Shore",
                    "agency": "Metra",
                    "distance": "2270.58",
                    "station_id": "5000",
                    "manhattan": "3171.62",
                    "lat": "41.884676",
                    "lng": "-87.6247309"
                },
                {
                    "gid": "376",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "2279.46",
                    "station_id": "260",
                    "manhattan": "2612.99",
                    "lat": "41.8858332",
                    "lng": "-87.6282889"
                },
                {
                    "gid": "234",
                    "name": "Clark\/Lake",
                    "line": "Blue, Pink, Green, Purple, Brown, Orange Lines",
                    "agency": "CTA",
                    "distance": "2305.32",
                    "station_id": "380",
                    "manhattan": "2747.09",
                    "lat": "41.8858551",
                    "lng": "-87.6314405"
                },
                {
                    "gid": "378",
                    "name": "State\/Lake",
                    "line": "Brown, Purple, Orange, Pink, Green Lines",
                    "agency": "CTA",
                    "distance": "2317.08",
                    "station_id": "260",
                    "manhattan": "2795.24",
                    "lat": "41.8858352",
                    "lng": "-87.6276277"
                },
                {
                    "gid": "684",
                    "name": "Union Station",
                    "line": "MD-West, MD-North, NCS, BNSF, Heritage, SWS",
                    "agency": "Metra",
                    "distance": "2442.79",
                    "station_id": "8000",
                    "manhattan": "2632.02",
                    "lat": "41.8791793",
                    "lng": "-87.6386341"
                },
                {
                    "gid": "685",
                    "name": "Union Station",
                    "line": "MD-West, MD-North, NCS, BNSF, Heritage, SWS",
                    "agency": "Metra",
                    "distance": "2498.70",
                    "station_id": "8000",
                    "manhattan": "3003.75",
                    "lat": "41.8781529",
                    "lng": "-87.6386368"
                },
                {
                    "gid": "683",
                    "name": "Union Station",
                    "line": "MD-West, MD-North, NCS, BNSF, Heritage, SWS",
                    "agency": "Metra",
                    "distance": "2698.26",
                    "station_id": "8000",
                    "manhattan": "3025.89",
                    "lat": "41.878764",
                    "lng": "-87.639522"
                }
            ]
        },
        "elapsed_time": 1.5829
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
