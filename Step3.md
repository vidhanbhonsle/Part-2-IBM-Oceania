# Calulate Delivery order using HERE Waypoint Sequence

### Add the following code before </script> tag

- Replace "REST_API_KEY" with your own

```javascript
var data = "";

 function showDetails(){
            let url = 'https://wse.ls.hereapi.com/2/findsequence.json'+
            '?apiKey=REST_API_KEY'+
            '&start='+destinations.truck.lat+','+destinations.truck.lng+
            '&destination0='+destinations.destination1.lat+','+destinations.destination1.lng+
            '&destination1='+destinations.destination2.lat+','+destinations.destination2.lng+
            '&destination2='+destinations.destination3.lat+','+destinations.destination3.lng+
            '&destination3='+destinations.destination4.lat+','+destinations.destination4.lng+
            '&destination4='+destinations.destination5.lat+','+destinations.destination5.lng+
            '&destination5='+destinations.destination6.lat+','+destinations.destination6.lng+
            '&destination6='+destinations.destination7.lat+','+destinations.destination7.lng+
            '&destination7='+destinations.destination8.lat+','+destinations.destination8.lng+
            '&destination8='+destinations.destination9.lat+','+destinations.destination9.lng+
            '&destination9='+destinations.destination10.lat+','+destinations.destination10.lng+
            '&mode=fastest;car;traffic:disabled'+
            '&improveFor=time'; 

            async function getapi(url){
            
            // Storing response 
            const response = await fetch(url); 
            data = await response.json(); 
            }
            getapi(url);
            
            var values = data.results[0].waypoints;
            
            var origin = null;
            
            for (i in values){
                a = values[i];
            
                var lat = a['lat'];
                var lng = a['lng'];
            
                if (!origin){
                    origin = {lat,lng};
                    continue;
                } else{
                    var destin = {lat,lng};
                    showRoute(origin,destin);
                    origin = destin;
                    console.log(JSON.stringify(origin) + ':::' + JSON.stringify(destin));
                    continue; 
                }
                }
            }
```
</br> 

[![Foo](/img/s4.png)](/Step4.md) 
