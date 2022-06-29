## Library Name:
Smart Watch 3

## Library Version:
1.0.0

## Compatibility
Supports OpenHarmony API version 8

## Library Overview:
Smart Watch three shows following functionalites;
- It fetches weather details based on the location of the user.
- Shows current date and time
- Calculates Number of steps walked  and Calories burned .

<hr>

### GitHub link: [Smart Watch three](https://github.com/Applib-OpenHarmony/SmartWatchThree)
<hr>



## Screenshot of the Library:
![lib](https://user-images.githubusercontent.com/61938892/176523931-5885bcb5-49a7-4f01-8a54-75f82697069f.PNG)




# Library Feature1:
### Description:
It fetches weather details from the API's
### Code Snippet:
```
fetchWeather: function () {
        var dataw = JSON.stringify(item);
        let weather_api_input = JSON.parse(dataw);
        let data;
        fetch.fetch({
            url: "https://api.openweathermap.org/data/2.5/weather?lat=" + weather_api_input[0].latitude + "&lon=" + weather_api_input[0].longitude + "&appid=" + weather_api_input[0].api_key,
            responseType: "json",
            method: 'GET',
            success: function (resp) {
                data = JSON.stringify(resp);
                console.info('Weather data fetch success. Resp: ' + data);
            },
            fail: function (data, code) {
                console.log("fail data: " + JSON.stringify(data) + " fail code: " + code);
            },
            complete: () => {
                const { main } = data.weather[0];
                this.weather = main;
                this.weather_description = main;
            }
        })
    },
    fetchNotification: function () {
        let data;
        fetch.fetch({
            complete: () => {
                this.notification = data.notification;
                this.min_progress_calories = data.min_progress_calories;
                this.min_progress_footSteps = data.min_progress_footSteps;
            }
        })
    }
```

### Screenshot:


### Flow chart description:
In fetchWeather function it will first fetches the locations details of the user i.e latitude and longitude,
 using openweather api fetches the weather details based on the latitude and longitude.


### Screenshot: 


# Library Feature2:
### Description: 
Calculates number of steps walked.

### Code Snippet:
```
function subscribePedometerSensor(context) {
    sensor.subscribeStepCounter({
        success: function (ret) {
            context.mySteps = ret.steps.toString()
        },
        fail: function (data, code) {
            console.log('Subscription failed. Code: ' + code + '; Data: ' + data)
        }
    })
}

```
### Screenshot:


![lol](https://user-images.githubusercontent.com/61938892/176526712-1ec566c4-166f-41c5-8505-60bdfcb2722c.PNG)

## Advanced feature that could be implemented in Future in this library: 
Calculating Blood Pressure and Calories Burned using respective API’s.


## Conclusion:
smart watch three calculates Number of steps walked, Calories burned, fetches date and time and weather details based on location and notifications.

