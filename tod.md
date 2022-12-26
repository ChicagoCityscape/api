# Details about the Address Snapshot API
The Address Snapshot API returns most of the data of an Address Snapshot Report on our website.

The endpoint is `https://chicagocityscape.com/api/index.php?`.

## Address Snapshot API Parameters

The parameters you must provide are grouped. A valid `key` parameter + parameters in Group 1, 2, 3, or 4 are required (Groups 1-4 help us locate the address or property you're seeking, and only one group is required). 

### Group 1 - PIN
Send a Cook County `pin` (14 digits, and it may begin with `0`) and the API will try to locate it in the parcels database. 

### Group 2 - Full address string
Use `query` and a full address (like `query=121 N La Salle St, Chicago, IL`) and the API will geocode it.

### Group 3 - Address parts 
Provide `address`, `city`, and `state` parameters. `zipcode` is optional. If `city` is empty or not provided, the API will assume `Chicago`. If `state` is empty or not provided, the API will assume `IL` (Illinois). 

### Group 4 - Coordinate
`lat` (latitude) and `lng` (longitude), in the EPSG 4326 (WGS84) projection. This coordinate will be reverse geocoded to determine the address. 

### Additional datasets
These optional query parameters will cause the API to grab additional data (this will increase the time response time). The additional options comprise:
- `get_permits=true` will look for building permits with a matching address in the City of Chicago; only works if an `address` is provided, but the API does not verify if that address is in Chicago before checking
- `get_violations=true` will look for building permits with a matching address in the City of Chicago; only works if an `address` is provided, but the API does not verify if that address is in Chicago before checking
- `get_incentives=true` will run Incentives Checker
- `skip_boundaries=true` will skip checking for Surrounding Places (ZIP code, ward, community area, custom boundaries, etc.)

## Notes

* A parcel that appears in the ````parcels_other```` property may also appear in the ````parcels_intersecting```` property if its attribute ````intersects```` is ````1````.
* Responses are cached for 72 hours.

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
        "parcels_address": [
            {
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
        "parcels_other": [],
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
        "boundaries": [
              {
                "name": "Illinois Center",
                "type": "custom",
                "metadata": null,
                "slug": "custom-illinois-center",
                "extra_info_jsonb": null,
                "area": "1401324.650069318",
                "area_intersection": "0"
              },
              {
                "name": "42-40",
                "type": "precinct",
                "metadata": "chicago",
                "slug": "precinct-chicago-42-40",
                "extra_info_jsonb": null,
                "area": "1650009.2205570592",
                "area_intersection": "0"
              },
              {
                "name": "Loop",
                "type": "communityarea",
                "metadata": "32",
                "slug": "communityarea-loop",
                "extra_info_jsonb": {
                  "mred_number": 8032
                },
                "area": "46335565.45867195",
                "area_intersection": "0"
              },
              {
                "name": "42nd Ward, Alder Brendan Reilly",
                "type": "ward",
                "metadata": "42",
                "slug": "ward-42",
                "extra_info_jsonb": null,
                "area": "71482506.26507778",
                "area_intersection": "0"
              },
              {
                "name": "Central Business District (CBD)",
                "type": "custom",
                "metadata": "Boundary from the Chicago Municipal Code, 9-4-010 Definitions.",
                "slug": "custom-chicago-central-business-district",
                "extra_info_jsonb": null,
                "area": "112280617.71752033",
                "area_intersection": "0"
              }
        ],
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
