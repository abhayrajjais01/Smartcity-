# 🏙️ Smart City Analytics Dashboard

A modern, real-time smart city dashboard that visualizes urban data using **proper, dedicated APIs** for each data type. Built with vanilla HTML, CSS, JavaScript, and Chart.js.

## ✨ Features

- **🌬️ Real-time Air Quality**: Live AQI, PM2.5, PM10, CO, NO₂, O₃, SO₂ data
- **🌡️ Weather Forecast**: Current temperature and 7-day forecast
- **🚗 Traffic Flow**: Real-time traffic speed and congestion levels
- **⚡ Energy/Carbon Intensity**: Live carbon intensity and energy consumption
- **📊 Interactive Charts**: Beautiful visualizations with Chart.js
- **🔍 Multi-City Support**: Search any city worldwide
- **📱 Responsive Design**: Works on desktop, tablet, and mobile

## 🛠️ Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Visualization**: Chart.js 4.4.0
- **HTTP Client**: Axios
- **APIs**: OpenWeatherMap, TomTom Traffic, Carbon Intensity API, Nominatim

## 📡 APIs Used (Proper APIs for Each Data Type)

### 1. **Air Quality Data**
- **API**: OpenWeatherMap Air Pollution API
- **Endpoint**: `https://api.openweathermap.org/data/2.5/air_pollution`
- **Data**: AQI (1-5 scale), PM2.5, PM10, CO, NO₂, O₃, SO₂
- **Free Tier**: 1,000 calls/day
- **Sign up**: https://openweathermap.org/api

### 2. **Weather Data**
- **API**: OpenWeatherMap Weather API
- **Endpoint**: `https://api.openweathermap.org/data/2.5/weather`
- **Data**: Temperature, humidity, weather conditions, 7-day forecast
- **Free Tier**: 1,000 calls/day
- **Sign up**: https://openweathermap.org/api

### 3. **Traffic Data**
- **API**: TomTom Traffic Flow API
- **Endpoint**: `https://api.tomtom.com/traffic/services/4/flowSegmentData`
- **Data**: Current speed, free flow speed, traffic congestion
- **Free Tier**: 2,500 requests/day
- **Sign up**: https://developer.tomtom.com/
- **Note**: Falls back to simulated data if API key not configured

### 4. **Energy/Carbon Intensity Data**
- **API**: UK Carbon Intensity API
- **Endpoint**: `https://api.carbonintensity.org.uk/regional`
- **Data**: Carbon intensity (gCO₂/kWh), generation mix
- **Free Tier**: Unlimited (no key required)
- **Note**: Works for UK locations; falls back to simulated data for other regions

### 5. **Geocoding**
- **API**: Nominatim (OpenStreetMap)
- **Endpoint**: `https://nominatim.openstreetmap.org/search`
- **Data**: Converts city names to coordinates
- **Free Tier**: Unlimited (no key required)

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection
- API keys (see Configuration section)

### Installation

1. **Clone or download this repository**:
   bash-
   git clone <repository-url>
   cd smart-city-v2
   

2. **Configure API keys** (see Configuration section below)

3. **Start a local server**:
   bash-
   # Using Python 3
   python3 -m http.server 8000
   
   # Using Node.js
   npx http-server
   
   # Using PHP
   php -S localhost:8000
   

4. **Open in browser**:
   
   http://localhost:8000
   

5. **Search for a city** and view real-time data!

## ⚙️ Configuration

### Required API Keys

1. **OpenWeatherMap API Key** (Required)
   - Sign up: https://openweathermap.org/api
   - Get your free API key
   - Open `script.js` and replace:
     javascript-
     OPENWEATHER_API_KEY: 'YOUR_API_KEY_HERE'
     

2. **TomTom Traffic API Key** (Optional)
   - Sign up: https://developer.tomtom.com/
   - Get your free API key (2,500 requests/day)
   - Open `script.js` and replace:
     javascript-
     TOMTOM_API_KEY: 'YOUR_TOMTOM_API_KEY'
     
   - **Note**: If not configured, the dashboard will use simulated traffic data

3. **Carbon Intensity API** (No key required)
   - Works automatically for UK locations
   - Falls back to simulated data for other regions

### API Key Setup in script.js

javascript-
const CONFIG = {
  OPENWEATHER_API_KEY: 'your_openweather_key_here',
  TOMTOM_API_KEY: 'your_tomtom_key_here', // Optional
  CARBON_INTENSITY_API: 'https://api.carbonintensity.org.uk',
  GEOCODING_API: 'https://nominatim.openstreetmap.org'
};


## 📊 Dashboard Components

### Key Metrics Cards
1. **Air Quality Index (AQI)**: 1-5 scale with color coding
2. **Temperature**: Current temperature in Celsius
3. **Traffic Flow**: Current speed and congestion status
4. **Energy Usage**: Carbon intensity level

### Charts
1. **Air Quality Trends**: 24-hour PM2.5 and PM10 forecast
2. **Temperature Forecast**: 7-day temperature forecast
3. **Traffic Patterns**: 24-hour traffic density simulation
4. **Energy Consumption**: 24-hour carbon intensity pattern

## 🧪 Testing with Postman

A Postman collection is included (`postman_collection.json`) for testing all API endpoints:

1. Import `postman_collection.json` into Postman
2. Replace API keys in the collection variables
3. Test each endpoint individually
4. Understand the data structure before using in the dashboard

### Collection Includes:
- OpenWeatherMap Air Pollution (current & forecast)
- OpenWeatherMap Weather (current & forecast)
- TomTom Traffic Flow
- UK Carbon Intensity API
- Nominatim Geocoding

## 📱 Usage

1. **Enter a city name** in the search box (e.g., "London", "New York", "Tokyo")
2. **Click "Search City"** or press Enter
3. **View real-time data**:
   - Air quality metrics and trends
   - Current temperature and forecast
   - Traffic flow information
   - Energy consumption patterns
4. **Explore charts** for detailed insights

## 🎨 Customization

### Change Color Scheme
Edit CSS variables in `style.css`:
css-
:root {
  --primary: #6366f1;
  --secondary: #8b5cf6;
  --success: #10b981;
  --warning: #f59e0b;
  --danger: #ef4444;
}


### Add More Cities
The dashboard supports any city worldwide. Just type the name and search!

### Modify Chart Types
Edit chart configurations in `script.js`:
javascript-
// Change from line to bar chart
type: 'bar' // or 'line', 'radar', 'doughnut', etc.

## 🐛 Troubleshooting

### No Data Loading
- **Check API keys**: Ensure OpenWeatherMap API key is configured
- **Check internet connection**: All APIs require internet access
- **Check browser console**: Press F12 to see error messages
- **Verify city name**: Try a major city name (e.g., "London", "Paris")

### Traffic Data Not Working
- **TomTom API key**: If not configured, simulated data is used
- **API limits**: Check if you've exceeded free tier limits
- **Fallback**: Dashboard automatically uses simulated data on error

### Energy Data Not Available
- **UK only**: Carbon Intensity API works for UK locations
- **Fallback**: Simulated data is used for non-UK locations
- **Alternative**: Consider using Electricity Maps API for global coverage

### CORS Errors
- **Use local server**: Don't open HTML file directly
- **Use http-server**: Run `python3 -m http.server 8000`
- **Check API endpoints**: Some APIs may have CORS restrictions

## 📝 Project Structure

smart-city-v2/
├── index.html              # Main HTML structure
├── style.css               # Styling and responsive design
├── script.js               # JavaScript logic and API calls
├── postman_collection.json # Postman API collection
└── README.md               # This file

## 🌟 Future Enhancements

-  Add more data sources (waste management, public transport)
-  Historical data comparison
-  Multiple city comparison view
-  Export data to CSV/JSON
-  Dark/light mode toggle
-  Push notifications for alerts
-  Map visualization with Leaflet.js
-  User preferences and saved cities
-  Real-time auto-refresh
-  Mobile app version

## 📄 API Rate Limits

| API | Free Tier | Rate Limit |
| OpenWeatherMap | 1,000 calls/day | 60 calls/minute |
| TomTom Traffic | 2,500 requests/day | No specified limit |
| Carbon Intensity | Unlimited | Fair use policy |
| Nominatim | Unlimited | 1 request/second |

## 🔒 Security Notes

- **Never commit API keys** to public repositories
- **Use environment variables** for production deployments
- **Rotate keys regularly** if exposed
- **Monitor API usage** to avoid unexpected charges

## 📧 Support

For issues or questions:
1. Check the browser console (F12) for errors
2. Review API documentation
3. Test endpoints in Postman
4. Verify API keys are correct

## 🙏 Acknowledgments

- [OpenWeatherMap](https://openweathermap.org/) - Weather and air quality data
- [TomTom](https://developer.tomtom.com/) - Traffic data
- [Carbon Intensity API](https://carbonintensity.org.uk/) - Energy data
- [Chart.js](https://www.chartjs.org/) - Chart library
- [Nominatim](https://nominatim.org/) - Geocoding service

## 📜 License

This project is open source and available for educational purposes.

**Built with integrity for Smart City Analytics**
