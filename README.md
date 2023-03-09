# Convert GPX  to GeoJSON.

This is a JavaScript library that lets projects convert [GPX](http://www.topografix.com/gpx.asp) to [GeoJSON](http://www.geojson.org/).


## [example](http://openlayers-cesium.com/demos/demo.html)

## html Link

> <script src="http://openlayers-cesium.com/demos/gpx2geojson.js" type="text/javascript"></script>

## Node install
 > npm install gpx2geojson -S

## ES Modules

```javascript
// The ES Module provides named exports, to import kml, gpx,
// and other parts of the module by name.
import gpx2geojson from "gpx2geojson";

let url='http://openlayers-cesium.com/demos/data/data2.gpx'
fetch(url)
	.then((response) => response.text())
	.then((gpxtext) => {
		let res = new DOMParser().parseFromString(gpxtext, "text/xml")
		console.log(gpx2GeoJSON.gpx(res))
	});

```

## Browser

```html
<script type="text/javascript">
        function loadGPX(url,id){
        	var xmlhttp;
        	if (window.XMLHttpRequest) { // code for IE7+, Firefox, Chrome, Opera, Safari
        		xmlhttp = new XMLHttpRequest();
        	} else { // code for IE6, IE5
        		xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
        	}
        	xmlhttp.open("GET", url, true);
        	
        	xmlhttp.setRequestHeader("Access-Control-Allow-Origin", "*");
        	xmlhttp.onreadystatechange = function() {
        		if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {				
        			let res = new DOMParser().parseFromString(xmlhttp.responseText, "text/xml")
        			console.log(gpx2GeoJSON.gpx(res))
        			document.getElementById(id).innerHTML = JSON.stringify(gpx2GeoJSON.gpx(res))				
        		}
        	}
        	xmlhttp.send();
        }
		loadGPX('http://openlayers-cesium.com/demos/data/data2.gpx','info2')
		
</script>
```


Using DOMParser: Convert string to xml 

```js
var dom = new DOMParser().parseFromString(xmlStr, "text/xml");  
```

