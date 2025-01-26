# weather_site
description: select your location and get weather, time and other info


## Step 1: Install the Necessary Tools
1. Download VSCode:
Go to [https://code.visualstudio.com/](https://code.visualstudio.com/) and install Visual Studio Code.
2. Install Node.js:
Go to [https://nodejs.org/](https://nodejs.org/) and install Node.js (this allows JavaScript to run locally).
3. Set up Git (optional, if not installed):
Download it from [https://git-scm.com/](https://git-scm.com/).

## Step 2: Create Your Project
1. Initialize the Project:
    
    - Open VSCode.
    - Create a new folder named weather_site.
    - Open the folder in VSCode: File > Open Folder.

2. Initialize Git:

    - Open the Terminal in VSCode (Ctrl + `` or View > Terminal).
    - Run the following commands to initialize Git:
```bash
git init
```

3. Create the Basic Files:

    - In VSCode, create the following files inside your weather_site folder:
        - index.html (the main web page)
        - style.css (for styling)
        - script.js (for JavaScript functionality)

## Step 3: Write the HTML (Dropdown Menu)
File: index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Weather Site</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Weather Site</h1>
  <label for="city-select">Select your city:</label>
  <select id="city-select">
    <option value="">--Select a city--</option>
    <option value="New York">New York</option>
    <option value="London">London</option>
    <option value="Tokyo">Tokyo</option>
    <option value="Sydney">Sydney</option>
  </select>
  <button id="get-weather">Get Weather</button>

  <div id="weather-info">
    <!-- Weather data will appear here -->
  </div>

  <script src="script.js"></script>
</body>
</html>
```

## Step 4: Add Styling
File: style.css
```css
body {
  font-family: Arial, sans-serif;
  margin: 20px;
  text-align: center;
}

h1 {
  color: #333;
}

#weather-info {
  margin-top: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  background-color: #f9f9f9;
}
```

## Step 5: Add JavaScript (Fetch Weather Data)
File: script.js
```js
// API key for OpenWeather (sign up at https://openweathermap.org/ for a free API key)
const API_KEY = 'your_api_key_here';

// Event listener for button click
document.getElementById('get-weather').addEventListener('click', () => {
  const city = document.getElementById('city-select').value;

  if (!city) {
    alert('Please select a city!');
    return;
  }

  // Fetch weather data
  fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`)
    .then(response => response.json())
    .then(data => {
      const weatherInfo = `
        <h2>Weather in ${data.name}</h2>
        <p><strong>Temperature:</strong> ${data.main.temp}°C</p>
        <p><strong>Humidity:</strong> ${data.main.humidity}%</p>
        <p><strong>Description:</strong> ${data.weather[0].description}</p>
      `;
      document.getElementById('weather-info').innerHTML = weatherInfo;
    })
    .catch(error => {
      console.error('Error fetching weather data:', error);
      alert('Could not fetch weather data. Please try again later.');
    });
});
```

## Step 6: Test Your Website
1. Open the terminal in your "IDE" (VSCode).
2. Run the command:
```bash
npx live-server
```
3. Open the provided link (e.g., `http://127.0.0.1:8080`) in your browser to view the site.
4. Select a city from the dropdown, click "Get Weather," and see the data!

## Step 7: Push to GitHub
1. Create a GitHub Repository:

    - Go to [https://github.com/](https://github.com/) and create a new repository named weather_site.

2. Push Your Code:

    - Run the following commands in the terminal:
```bash
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/weather_site.git
git push -u origin main
```

## Step 8: Deploy the Website
1. Use GitHub Pages for free hosting:
    - Go to your GitHub repository settings.
    - Scroll to "Pages," select the main branch, and save.
    - Your website will be available at `https://yourusername.github.io/weather_site`.

## Summary
You’ve built a simple weather website with:

- An HTML dropdown menu for city selection.
- CSS styling to make it look clean.
- JavaScript to fetch and display real-time weather data. 
