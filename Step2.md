# Place markers on the map with custom images


## Adding a position marker using map object of Interactive maps API
- Provide the position for all the delivery locations and delivery vehicle

```javascript
        // Get your current position from wego.here.com
          var destinations = { 
            "destination1": {lat: -37.778512, lng: 144.974306}, 
            "destination2": {lat: -37.793962, lng: 144.990440}, 
            "destination3": {lat: -37.811640, lng: 144.957030}, 
            "destination4": {lat: -37.775800, lng: 144.933553},
            "destination5": {lat: -37.709759, lng: 144.974606}, 
            "destination6": {lat: -37.714317, lng: 144.967514},
            "destination7": {lat: -37.722485, lng: 144.973918}, 
            "destination8": {lat: -37.756360, lng: 144.906203}, 
            "destination9": {lat: -37.818924, lng: 144.888215},
            "destination10": {lat: -37.818924, lng: 144.889215},  
            "truck": {lat: -37.808290, lng: 144.980248}
            }; 
```

- Edit the centre location on the map to see from trucks perspective

```javascript
        // Get your current position from wego.here.com
        var map = new H.Map(
              document.getElementById('mapContainer'),
              defaultLayers.vector.normal.map,
              {
                  zoom: 12,
                  center: destinations.truck,
              });
```

- Add a folder named "img" inside the folder "Interactive_Map_With_HERE"
- Inside the folder "img", save the image you want as the icon for truck and homes
- You can also download the ones I used for [home](img/home.png) and [truck](img/truck.png)
- Add the following code before </script> tag

```javascript
    // create an icon for the marker. Choose any image you want. I created mine using draw.io     
        var homeIcon = new H.map.Icon('img/home.png'); 
        var truckIcon = new H.map.Icon('img/truck.png'); 
                  
        // Create a marker using the previously instantiated icon
        var posMarker1 = new H.map.Marker(destinations.destination1,{icon:homeIcon});
        var posMarker2 = new H.map.Marker(destinations.destination2,{icon:homeIcon});
        var posMarker3 = new H.map.Marker(destinations.destination3,{icon:homeIcon});
        var posMarker4 = new H.map.Marker(destinations.destination4,{icon:homeIcon});
        var posMarker5 = new H.map.Marker(destinations.destination5,{icon:homeIcon});
        var posMarker6 = new H.map.Marker(destinations.destination6,{icon:homeIcon});
        var posMarker7 = new H.map.Marker(destinations.destination7,{icon:homeIcon});
        var posMarker8 = new H.map.Marker(destinations.destination8,{icon:homeIcon});
        var posMarker9 = new H.map.Marker(destinations.destination9,{icon:homeIcon});
        var posMarker10 = new H.map.Marker(destinations.destination10,{icon:homeIcon});
        var posMarkerTruck = new H.map.Marker(destinations.truck,{icon:truckIcon});

        // Add the marker to the map 
        map.addObject(posMarker1);
        map.addObject(posMarker2);
        map.addObject(posMarker3);
        map.addObject(posMarker4);
        map.addObject(posMarker5);
        map.addObject(posMarker6);
        map.addObject(posMarker7);
        map.addObject(posMarker8);
        map.addObject(posMarker9);
        map.addObject(posMarker10);
        map.addObject(posMarkerTruck);
```

[![Foo](/img/s3.png)](/Step3.md) 

