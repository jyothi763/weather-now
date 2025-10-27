# weather-now
# 🌤 Weather Now
const weatherCodes = {
  0: { desc: "Clear Sky", icon: "☀" },
  1: { desc: "Mainly Clear", icon: "🌤" },
  2: { desc: "Partly Cloudy", icon: "⛅" },
  3: { desc: "Overcast", icon: "☁" },
  45: { desc: "Fog", icon: "🌫" },
  48: { desc: "Depositing Rime Fog", icon: "🌫" },
  51: { desc: "Light Drizzle", icon: "🌦" },
  61: { desc: "Slight Rain", icon: "🌧" },
  71: { desc: "Slight Snow", icon: "🌨" },
  95: { desc: "Thunderstorm", icon: "⛈" },
};

function WeatherCard({ weather, unit }) {
  const { desc, icon } = weatherCodes[weather.weathercode] || {
    desc: "Unknown",
    icon: "❓",
  };

  const temp =
    unit === "celsius"
      ? weather.temperature
      : (weather.temperature * 9) / 5 + 32;

  return (
    <div className="bg-white shadow-xl rounded-2xl p-6 text-center mt-6 w-80 transition hover:scale-105">
      <h2 className="text-xl font-semibold mb-2">
        {weather.city}, {weather.country}
      </h2>
      <div className="text-6xl mb-2">{icon}</div>
      <p className="text-lg font-semibold mb-1">{desc}</p>
      <p className="text-4xl font-bold mb-2">
        {temp.toFixed(1)}°{unit === "celsius" ? "C" : "F"}
      </p>
      <p>💨 Wind: {weather.windspeed} km/h</p>
      <p>🧭 Direction: {weather.winddirection}°</p>
      <p className="text-sm text-gray-500 mt-3">
        Last updated: {new Date().toLocaleTimeString()}
      </p>
    </div>
  );
}

export default WeatherCard;
A responsive React web app that displays real-time weather information using the Open-Meteo API.

## ✨ Features
- Search weather by city name
- Displays temperature, wind, and direction
- Weather icons and condition descriptions
- °C / °F toggle
- Loading spinner
- Saves last searched city (localStorage)
- Last updated time

## 🧰 Tech Stack
- React + Vite
- Tailwind CSS
- Open-Meteo API

## 🚀 Setup
1. Clone the repository  
2. Run npm install  
3. Run npm run dev to start  

## 🗺 API References
- [Geocoding API](https://geocoding-api.open-meteo.com/v1/search?name={city})
- [Weather API](https://api.open-meteo.com/v1/forecast)
