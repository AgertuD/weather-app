# Travel Advisory & Weather Website

## Overview
This project is a web-based application that provides travel advisory information and real-time weather updates. It fetches data from external APIs and displays relevant information to help users make informed travel decisions.

## Features
- Search for travel advisories by country
- Get real-time weather updates for selected destinations
- Responsive and user-friendly UI
- API-based data fetching and dynamic content rendering

## Technologies Used
- **Frontend:** HTML, CSS, JavaScript
- **APIs Used:**
  - [Weather API](https://www.weatherapi.com/) - Provides real-time weather data
  - [Travel Advisory API](https://www.traveladvisory.info/) - Offers travel safety information
- **Deployment:** Hosted on two web servers with a load balancer

## Installation & Local Setup
To run the project locally, follow these steps:

1. **Clone the repository:**
   ```sh
   git clone https://github.com/your-username/travel-advisory-weather.git
   cd travel-advisory-weather
   ```

2. **Set up API keys:**
   - Sign up at [Weather API](https://www.weatherapi.com/) and get an API key.
   - Sign up at [Travel Advisory API](https://www.traveladvisory.info/) and obtain an API key.
   - Create a `.env` file in the project root and add your API keys:
     ```sh
     WEATHER_API_KEY=your_weather_api_key
     TRAVEL_ADVISORY_API_KEY=your_travel_advisory_api_key
     ```

3. **Run a local development server:**
   - Open `index.html` in a browser
   - Alternatively, use a simple Python server:
     ```sh
     python -m http.server
     ```
   - Visit `http://localhost:8000` in your browser

## Deployment Instructions
This application is deployed on two web servers (Web01 and Web02) with a load balancer (Lb01). Follow these steps for deployment:

1. **Prepare the Servers:**
   - Ensure both Web01 and Web02 have Apache/Nginx installed.
   - Upload the project files to `/var/www/html/`.
   
2. **Configure the Load Balancer:**
   - Set up Nginx/HAProxy to distribute traffic between Web01 and Web02.
   - Example Nginx config snippet:
     ```nginx
     upstream backend {
         server Web01_IP;
         server Web02_IP;
     }

     server {
         listen 80;
         location / {
             proxy_pass http://backend;
         }
     }
     ```

3. **Restart Services:**
   ```sh
   sudo systemctl restart nginx
   ```

4. **Access the Website:**
   - Visit `http://Lb01_IP` to access the deployed application.

## Challenges & Solutions
### Challenge 1: API Rate Limits
- **Problem:** Limited API requests per hour.
- **Solution:** Implemented caching to reduce redundant API calls.

### Challenge 2: Cross-Origin Resource Sharing (CORS) Issues
- **Problem:** Some API requests were blocked due to CORS policies.
- **Solution:** Used a proxy server and enabled CORS headers in API requests.

### Challenge 3: Load Balancer Configuration
- **Problem:** Ensuring smooth traffic distribution.
- **Solution:** Optimized the load balancer settings and monitored server logs for insights.

## Credits & Acknowledgements
- **APIs Used:**
  - [Weather API](https://www.weatherapi.com/)
  - [Travel Advisory API](https://www.traveladvisory.info/)
- **Libraries & Resources:**
  - Bootstrap for UI styling
  - Fetch API for asynchronous requests
  - Online tutorials and documentation from MDN Web Docs and W3Schools

## Author
[Your Name] - Software Engineering Student

