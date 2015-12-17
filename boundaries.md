# Chicago Cityscape API

## Place boundary endpoints
The API will return the boundaries as GeoJSON for any one of our 2,100 "Places", which includes neighborhoods, community areas, wards, and custom drawn areas like neighborhood associations. 

### "List all places" endpoint
Get a list of all the possible places for which you can get boundaries. 

* Example: [all places](http://www.chicagocityscape.com/php/api.places.php?method=allplaces): ````http://www.chicagocityscape.com/php/api.places.php?method=allplaces````

### Search endpoint
If you want to search for a Place by keyword, specify a "query" parameter and make the method "search". 

* Example: [Avondale](http://www.chicagocityscape.com/php/api.places.php?query=avondale&method=search): ````http://www.chicagocityscape.com/php/api.places.php?query=avondale&method=search````

### Specific Place endpoint
If you know the Place slug then you can ask for it directly. 

* Example: [Avondale, the community area](http://www.chicagocityscape.com/php/api.map.php?method=boundary&place=communityarea-avondale): ````http://www.chicagocityscape.com/php/api.map.php?method=boundary&place=communityarea-avondale````
* Example: [Avondale, the neighborhood](http://www.chicagocityscape.com/php/api.map.php?method=boundary&place=neighborhood-avondale): ````http://www.chicagocityscape.com/php/api.map.php?method=boundary&place=neighborhood-avondale````
