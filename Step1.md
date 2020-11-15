
# Create and Render a Map and customise it

## Copy the code below in a file 'index.html'
- Replace "YOUR_JS_API_KEY" with your API Key

``` html
<!DOCTYPE html>
<html>
    <head>
        <title>Delivery Solution</title>
        <!-- SCRIPTS -->
        <meta name="viewport" charset="UTF-8" content="initial-scale=1.0, width=device-width" />
        <script type="text/javascript" src="https://js.api.here.com/v3/3.1/mapsjs-core.js"></script>
        <script type="text/javascript" src="https://js.api.here.com/v3/3.1/mapsjs-service.js"></script>
        <script type="text/javascript" src="https://js.api.here.com/v3/3.1/mapsjs-ui.js"></script>
        <script type="text/javascript" src="https://js.api.here.com/v3/3.1/mapsjs-mapevents.js"></script>
        <link rel="stylesheet" type="text/css" href="https://js.api.here.com/v3/3.1/mapsjs-ui.css"/>
    </head>

    <body>
        <div id="mapContainer" style="width: 98vw; height: 91vh; display: block; margin: 0 auto; border: solid 2px black; margin-top: 5px;" > </div>
        <input type="button" onclick="showDetails()" value = "Show Details" style="width: 200px; height: 30px; border: 2px solid black; display: block; margin: 0 auto; margin-top: 10px;">
        <div id="panel" style="width: 30vw; background: #39B6B3; color: white; margin-top: 20px;display: block; margin: 0 auto;"></div>
     </body>
    
    <script>
        var platform = new H.service.Platform({
            apikey: "YOUR_JS_API_KEY"   
        });

        // Obtain the default map types from the platform object:
        var defaultLayers = platform.createDefaultLayers();

        // Instantiate (and display) a map object:
        var map = new H.Map(
            document.getElementById('mapContainer'),
            defaultLayers.vector.normal.map,
            {
                zoom: 11,
                center: {lat: 12.95677, lng: 77.73164}
            });

        var ui = H.ui.UI.createDefault(map, defaultLayers, 'en-US');

        var mapEvents = new H.mapevents.MapEvents(map);
        var behavior = new H.mapevents.Behavior(mapEvents);

    </script>
</html>
```

## Customize the map with YAML file
- Add the following code before </script> tag

```javascript
        function setStyle(map){
              // get the vector provider from the base layer
              var provider = map.getBaseLayer().getProvider();
              var style = new H.map.Style('https://heremaps.github.io/maps-api-for-javascript-examples/change-style-at-load/data/dark.yaml',
                'https://js.api.here.com/v3/3.1/styles/omv/');
              // set the style on the existing layer
              provider.setStyle(style);
            }
          setStyle(map);
```

[![Foo](/img/s2.png)](/Step2.md) 


