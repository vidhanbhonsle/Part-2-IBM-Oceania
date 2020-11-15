
# Draw a route for delivery


```javascript

// Get an instance of the routing service for using the routing API
var router = platform.getRoutingService();

function showRoute(origin,destin){          
        // Create the parameters for the routing request:
        var routingParameters = {
          'routingMode': 'fast',
          'transportMode': 'car',
          // The start point of the route:
          'origin': origin.lat + ',' + origin.lng,
          // The end point of the route:
          'destination': destin.lat + ',' + destin.lng,
          // Include the route shape in the response
          'return': 'polyline'
        };

        // Define a callback function to process the routing response:
        var onResult = function(result) {
          // ensure that at least one route was found
          if (result.routes.length) {
            result.routes[0].sections.forEach((section) => {
                // Create a linestring to use as a point source for the route line
                let linestring = H.geo.LineString.fromFlexiblePolyline(section.polyline);

                // Create a polyline to display the route:
                // let routeLine = new H.map.Polyline(linestring, {
                //   style: { strokeColor: 'red', lineWidth: 3 }
                // });

                // Create an outline for the route polyline:
                var routeOutline = new H.map.Polyline(linestring, {
                  style: {
                    lineWidth: 10,
                    strokeColor: 'rgba(255, 0, 0, 0.7)',
                    lineTailCap: 'arrow-tail',
                    lineHeadCap: 'arrow-head'
                  }
                });
                // Create a patterned polyline:
                var routeArrows = new H.map.Polyline(linestring, {
                  style: {
                    lineWidth: 10,
                    fillColor: 'white',
                    strokeColor: 'rgba(255, 255, 255, 1)',
                    lineDash: [0, 2],
                    lineTailCap: 'arrow-tail',
                    lineHeadCap: 'arrow-head' }
                  }
                );
                // create a group that represents the route line and contains
                // outline and the pattern
                var routeLine = new H.map.Group();
                routeLine.addObjects([routeOutline, routeArrows]);


                // Add the route polyline and the two markers to the map:
                map.addObject(routeLine);

                // Set the map's viewport to make the whole route visible:
                map.getViewModel().setLookAtData({bounds: routeLine.getBoundingBox()});
            
            });
          }
          
        };
        router.calculateRoute(routingParameters, onResult,
    function(error) {
        alert(error.message);
        });
        }
```
[![Foo](/img/s5.png)](/Step5.md) 

