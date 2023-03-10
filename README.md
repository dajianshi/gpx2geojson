# Convert GPX  to GeoJSON.

This is a JavaScript library that lets projects convert [GPX](http://www.topografix.com/gpx.asp) to [GeoJSON](http://www.geojson.org/).


## [example](http://openlayers-cesium.com/demos/demo.html)

#link and install 

## html Link

> <script src="http://openlayers-cesium.com/demos/gpx2geojson.js" type="text/javascript"></script>

## Node install
 > npm install gpx2geojson -S

# gpx data demos

## data1
```
<?xml version="1.0" encoding="UTF-8"?><gpx version="1.1" creator="dajianshi">
  <trk>
    <trkseg>
      <extensions>
        <MM>true</MM>
      </extensions>
      <trkpt lat="31.9410515" lon="118.8261001">
        <ele>81.6</ele>
        <time>2023-02-24T07:48:06Z</time>
        <extensions>
          <cellular>{"key":"SIM11","value":"11"}</cellular>
          <accuracy>15.194930076599121</accuracy>
          <speed>24.09</speed>
          <direction>331.8900146484375</direction>
        </extensions>
      </trkpt>
      <trkpt lat="31.9412279" lon="118.8259888">
        <ele>79.9</ele>
        <time>2023-02-24T07:48:06Z</time>
        <extensions>
          <cellular>{"key":"SIM22","value":"122"}</cellular>
          <accuracy>14.537370681762695</accuracy>
          <speed>24.22</speed>
          <direction>326.8900146484375</direction>
        </extensions>
      </trkpt>
    </trkseg>
  </trk>
</gpx>

```

## data2
```
<?xml version="1.0"?>
<gpx
 version="1.0"
 creator="ExpertGPS 1.1 - http://www.topografix.com"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns="http://www.topografix.com/GPX/1/0"
 xsi:schemaLocation="http://www.topografix.com/GPX/1/0 http://www.topografix.com/GPX/1/0/gpx.xsd">
<time>2002-02-27T17:18:33Z</time>
<bounds minlat="42.401051" minlon="-71.126602" maxlat="42.468655" maxlon="-71.102973"/>

<wpt lat="42.445359" lon="-71.122845">
 <ele>61.649902</ele>
 <time>2001-11-28T21:05:28Z</time>
 <name>5144SUMMIT</name>
 <desc><![CDATA[Summit]]></desc>
 <sym>Summit</sym>
 <type><![CDATA[Summit]]></type>
</wpt>
<wpt lat="42.441727" lon="-71.121676">
 <ele>67.360800</ele>
 <time>2001-06-02T00:18:16Z</time>
 <name>5150TANK</name>
 <cmt>WATER TANK</cmt>
 <desc><![CDATA[Water Tank]]></desc>
 <sym>Museum</sym>
 <type><![CDATA[Water Tank]]></type>
</wpt>
<rte>
 <name>BELLEVUE</name>
 <desc><![CDATA[Bike Loop Bellevue]]></desc>
 <number>1</number>
<rtept lat="42.430950" lon="-71.107628">
 <ele>23.469600</ele>
 <time>2001-06-02T00:18:15Z</time>
 <name>BELLEVUE</name>
 <cmt>BELLEVUE</cmt>
 <desc><![CDATA[Bellevue Parking Lot]]></desc>
 <sym>Parking Area</sym>
 <type><![CDATA[Parking]]></type>
</rtept>
<rtept lat="42.431240" lon="-71.109236">
 <ele>26.561890</ele>
 <time>2001-11-07T23:53:41Z</time>
 <name>GATE6</name>
 <desc><![CDATA[Gate 6]]></desc>
 <sym>Trailhead</sym>
 <type><![CDATA[Trail Head]]></type>
</rtept>
<rtept lat="42.434980" lon="-71.109942">
 <ele>45.307495</ele>
 <time>2001-11-07T23:53:41Z</time>
 <name>PANTHRCAVE</name>
 <desc><![CDATA[Panther Cave]]></desc>
 <sym>Tunnel</sym>
 <type><![CDATA[Tunnel]]></type>
</rtept>
</rte>
</gpx>
```

# How to use

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
		console.log(toGeoJSON.gpx(res))
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

