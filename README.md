# Chicago Cityscape API

The Chicago Cityscape API returns data about an address in Illinois or a Property Index Number (PIN) in Cook County, Illinois. Returned data can including information about elected officials, TIF districts, nearby CTA & Metra stations, and potential financial incentives for that address or PIN. The most information is returned for Chicago addresses. 

Using the API requires a `key` which is available to certain members and can be found on your [Account](http://chicagocityscape.com/account.php) page.

## Three API services/endpoints

### 1. Address Snapshot API 

[Address Snapshot API documentation](tod.md)

The "Address Snapshot API" returns the same information that you get in an [Address Snapshot Report](http://chicagocityscape.com/address.php).
````
https://www.chicagocityscape.com/api/index.php
````

*The Address Snapshot API was previously called the TOD API.*

#### Sample API calls
Get a response for an address in Chicago. If the API call doesn't have coordinates, the API will automatically geocode the address. Provide coordinates using `lat` and `lng` parameters (this will also marginally speed up the response).
````
https://www.chicagocityscape.com/api/index.php?address=333 N Michigan Ave&city=Chicago&state=IL&key=XXX
````

Get a response for a PIN in Cook County. If the PIN is found but doesn't have a record in the Cook County Parcel 2019 GIS layer, then the PIN is geocoded. 
````
https://www.chicagocityscape.com/api/index.php?pin=13364210400000&key=XXX
````

### 2. Parcels API

[Parcels API documentation](parcels.md).

This API returns a GeoJSON dataset of Cook County parcels within a radius (in feet) of a WGS84 geographic coordinate, inside a bounding box passed to the API as a GeoJSON polygon, or inside or within a radius (in feet) of one of our thousands of Place Snapshots (using the `slug` parameter). 
````
/* The endpoint URL...*/
https://www.chicagocityscape.com/api/parcels.php
````

### 3. Boundaries API 
Visit [Boundaries (Places)](https://github.com/ChicagoCityscape/api/blob/master/boundaries.md) for details on how to get GeoJSON for wards, community areas, neighborhoods, Chicago Public Schools attendance areas, and other kinds of boundaries.


## Troubleshooting
- If you are using cURL to access the API and you are receiving results but unexpected results, try sending the parameters as a JSON payload, or "-d" properties, rather then encoding them in the URL.
