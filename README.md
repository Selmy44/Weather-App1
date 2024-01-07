<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Weather App</title>
</head>
<body>
  <h1>Weather App</h1>
  <input type="text" id="city" placeholder="Enter city name">
  <button onclick="getWeather()">Get Weather</button>
  <div id="weather-info"></div>

  <script>
    async function getWeather() {
      const city = document.getElementById('city').value;
      const apiKey = 'YOUR_API_KEY'; // Replace with your API key from a weather service provider
      const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

      try {
        const response = await fetch(apiUrl);
        const data = await response.json();
        
        const weatherInfo = document.getElementById('weather-info');
        weatherInfo.innerHTML = `
          <h2>${data.name}, ${data.sys.country}</h2>
          <p>Temperature: ${data.main.temp}°C</p>
          <p>Weather: ${data.weather[0].description}</p>
        `;
      } catch (error) {
        console.error('Error fetching data:', error);
        const weatherInfo = document.getElementById('weather-info');
        weatherInfo.innerHTML = 'Error fetching weather data';
      }
    }
  </script>
</body>
</html>
