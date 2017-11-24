# Chicago Cityscape API

## Place boundary endpoints
The API will return the boundaries as JSON for any one of our [22,200+ "Places"](http://www.chicagocityscape.com/maps/index.php), which includes neighborhoods, community areas, wards, and custom drawn areas like neighborhood associations. 

### "List all Places" endpoint: method=allplaces
Get a list of all the possible Places for which you can get boundaries. Does not return geometry.

* Example: [all places](http://www.chicagocityscape.com/php/api.places.php?method=allplaces): ````http://www.chicagocityscape.com/php/api.places.php?method=allplaces````

### Search endpoint: method=search
If you want to search for a Place by keyword, specify a "query" parameter and make the method "search". Does not return geometry.

* Example: [Avondale](http://www.chicagocityscape.com/php/api.places.php?query=avondale&method=search): ````http://www.chicagocityscape.com/php/api.places.php?query=avondale&method=search````

### Specific endpoint: method=boundary
If you know a Place's ````slug```` (because you got it from the "List all Places" endpoint) then you can ask for it directly. Returns geometry as GeoJSON. 

* Example: [Avondale, the community area](http://www.chicagocityscape.com/php/api.map.php?method=boundary&place=communityarea-avondale): ````http://www.chicagocityscape.com/php/api.map.php?method=boundary&place=communityarea-avondale````
* Example: [Avondale, the neighborhood](http://www.chicagocityscape.com/php/api.map.php?method=boundary&place=neighborhood-avondale): ````http://www.chicagocityscape.com/php/api.map.php?method=boundary&place=neighborhood-avondale````
