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