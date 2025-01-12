<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.2/css/all.css" integrity="sha384-fnmOCqbTlWIlj8LyTjo7mOUStjsKC4pOpQbqyi7RrhN7udi9RwhKkMHpvLbHG9Sr" crossorigin="anonymous">
    <title>Document</title>
    <style>
        html {
          font-family: Arial;
          display: inline-block;
          margin: 0px auto;
          text-align: center;
         }
         h2 { font-size: 3.0rem; }
         p { font-size: 3.0rem; }
         .units { font-size: 1.2rem; }
         .dht-labels{
           font-size: 1.5rem;
           vertical-align:middle;
           padding-bottom: 15px;
         }
       </style>
</head>
<body>
    
<h2>ESP8266 DHT Server</h2>
  <p>
    <i class="fas fa-thermometer-half" style="color:#059e8a;"></i> 
    <span class="dht-labels">Temperature</span> 
    <span id="suhu">%TEMPERATURE%</span>
    <sup class="units">&deg;C</sup>
  </p>
  <p>
    <i class="fas fa-tint" style="color:#00add6;"></i> 
    <span class="dht-labels">Humidity</span>
    <span id="kel">%HUMIDITY%</span>
    <sup class="units">%</sup>
  </p>
<script src="libfire.js" ></script>
<script>

var config = {
  apiKey: "AIzaSyD7zG8U8Q5-UxXUk1yZqlGeqWe2Vihs1oc",
  authDomain: "adidaengclub.firebaseapp.com",
  databaseURL: "https://adidaengclub-default-rtdb.firebaseio.com",
  projectId: "adidaengclub",
  storageBucket: "adidaengclub.firebasestorage.app",
  messagingSenderId: "15490031968",
  appId: "1:15490031968:web:62e18eb89c792a29697e05",
  measurementId: "G-8FYBTLSRQG"

  };
firebase.initializeApp(config);
var db = firebase.database();
var temp = db.ref("/temp");
var kel = db.ref("/hum");
temp.on("value", function(snapshot) {document.getElementById('suhu').innerHTML=  (snapshot.val());});
kel.on("value", function(snapshot) {document.getElementById('kel').innerHTML=  (snapshot.val());});

</script>
</body>
</html>
