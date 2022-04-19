<img width="1440" alt="Screen Shot 2022-03-20 at 3 20 33 PM" src="https://user-images.githubusercontent.com/75461281/159184476-86244e8e-c4b9-45a4-bf84-a93064bad121.png">

<img width="1440" alt="Screen Shot 2022-03-19 at 12 20 03 PM" src="https://user-images.githubusercontent.com/75461281/159131488-e97d3c94-c978-4ea8-9a5e-42085c69c22a.png">

### HamaraWeather
This is app will be using the accu weather api to display weather conditions in any city of the world. In urdu language, 'Hamara' means 'our', you can translate the name as 'OurWeather'app 😄 🇵🇰
### file folder
The files in the project contain an index.html file, a styles.css file, and a folder for javascript. The folder, scripts has two files, app.js for DOM manipulation and forecast.js for API calls, async and await code. 

#### Index.html
the index.html file has links to bootstarp cdn, link to our styles.css file and in the body tag script tag to link our javascript folder:
```
 <script src="scripts/app.js"></script>
 ```
 First we created div tag in our body, give this div a class of container, with margin on Y-axis and x-axis, like so:
 ```
 <div class="container my-5 mx-auto">
 ```
 Then we created a headline in our h5 tag, giving it a class of text-muted for a lighter text appearance, and text-center :
 
 ```
 <h1 class="text-muted text-center my-4">HamaraWeather</h1>
 ```
 Then comes our form element, this form will ask the users to enter a city name in the search bar. the form has a class of chgange-location to apply DOM manipulation on it later. It has a text inout type with name porperty set city to match with the label for this input. 

 ```
 <form class="change-location my-4 text-center text-muted">
      <label for="city">Enter a location for weather information</label>
      <input type="text" name="city" class="form-control p-4">
    </form>
  ```  
    After this, I have created a card to display a picture of the time of the day, I placed a placeholder image for that, then I created an icon tag, followed by city name and two span tags to display temperatutre. 
```
    <div class="text-muted text-uppercase text-center details">
         <h5 class="my-3">City name</h5>
         <div class="my-3">Weather Condition</div>
         <div class="display-4 my-4">
           <span>temp</span>
           <span>&deg;c</span>
```
#### styles.css
In our css file, we have given the background a light gery color, some etter spacing and font sizing. We have also styled our container to ensure that everything is contained and not too wide with these simple styling techniques:
``` 
body{
  background: #eeedec;
  letter-spacing: 0.2em;
  font-size: 0.8em;
}
.container{
  max-width: 400px;
}
```

### forecast.js
The code in the file deals with interacting with the api calls, its makes the call to the api, and get data. There two functions in the file, one gets the data froim teh api calls, store the city id and the second function received that city id from the weatherdets and show the weather (current) condition in that city. 
````
onst getWeather = async (id) => {

  const base = 'http://dataservice.accuweather.com/currentconditions/v1/';

  const query = `${id}?apikey=${key}`;

  const response = await fetch(base + query);
  const data = await response.json();

  return data[0];

};
````
The second function grabs the city id and makes another call to the api to gets the current weather conditions for that city:
```
const getCity = async (city) => {
  
  const base = 'http://dataservice.accuweather.com/locations/v1/cities/search';
  const query = `?apikey=${key}&q=${city}`;

  const response = await fetch(base + query);
  const data = await response.json();
 return (data[0]);

};
```
### Introducing class in the project
Finally, we introduce the class in JS forcast file, we crrate a forcast class that has the constructor to set up the properties for the class. These properties are the URL base we need to get data for city and weather.
```
class Forecast{
  constructor(){
    this.key = 'MGwKbSzGkvTQ5ZfzmJlijcpCLvmRuJmV';
    this.weatherURI = 'http://dataservice.accuweather.com/currentconditions/v1/';
    this.cityURI = 'http://dataservice.accuweather.com/locations/v1/cities/search';
  }
  ````
  Then we async methods insiode the class to get city and weather. 
  ```
 async updateCity(city){
    const cityDets = await this.getCity(city);
    const weather = await this.getWeather(cityDets.Key);
    return {cityDets,  weather };
  }
  async getCity(city){
      const query = `?apikey=${this.key}&q=${city}`;
      const response = await fetch(this.cityURI + query);
      const data = await response.json();
      return data[0];
  }

  async getWeather(id){
    const query = `${id}?apikey=${this.key}`;
    const response = await fetch(this.weatherURI + query);
    const data = await response.json();
    return data[0];
  }
}
```
In our app.js file we created a new instance of forcast class with those porperties and methods attached to it, and change the call to updateCity with forcast class and passing the city as argument, thus starting the chain of the functions to get and display the data in our app. 