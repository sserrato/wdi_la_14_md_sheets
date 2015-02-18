#GOOGLE MAPS API CHEAT SHEET

[Back To The Index]()<br>
<br>

1. Obtain an API key
[https://developers.google.com/maps/documentation/javascript/tutorial](https://developers.google.com/maps/documentation/javascript/tutorial)

2. Visit Google API Console: [https://code.google.com/apis/console
](https://code.google.com/apis/console
)
Click services link in menu on left hand side
Activate Google Maps Javascript API 3 service.<br>
<br>
*Click API access link to get your API*

3. Create a new Rails project
Go to app > views > layouts and create a partial called: ***_map.html.erb*** Add the script tag making use of your specific API key:

```javascript
<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=API_KEY"></script>
Add other script to <head> in application.html.erb
<script type="text/javascript">  function initialize() { var mapOptions = { center: { lat: -34.397, lng: 150.644},zoom: 8}; var map = new google.maps.Map(document.getElementById('map-canvas'), mapOptions); } google.maps.event.addDomListener(window, 'load', initialize);</script>
```
4. Create a partial, _maps.html.erb, include a reference for the  div and render the map in any view you want it to display.
