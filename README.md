# CookieClip IRL Overlay

A lightweight, battery-efficient, client-side browser overlay engineered for the **IRL Pro** Android live streaming app and OBS / PRISM Live Studio.

It automates location display with built-in **OPSEC / privacy protection**, snapping your coarse GPS position to the nearest major metropolitan area (e.g., Beverly Hills, Santa Monica, or Glendale displays as **"Los Angeles, CA"**), alongside real-time temperature and weather icons updated every 10 minutes.

---

## 🌟 Features

- **Coarse Geo-Fencing & OPSEC:** Snaps approximate GPS coordinates to predefined anchor metropolitan hubs using great-circle haversine calculation. Never leaks precise streets, venues, or suburban neighborhoods on stream.
- **Zero API Keys Required:** Integrates with [Open-Meteo](https://open-meteo.com/) for real-time weather code mappings and Fahrenheit temperatures.
- **Ultra-Low Battery & Data Footprint:** Requests coarse network location (`enableHighAccuracy: false`) with a 10-minute caching lifecycle (`maximumAge: 600000`) and a 10-minute poll interval (`600,000 ms`).
- **Live Accurate Clock:** Smooth 1-second interval timestamp adhering to your original format (`MMM dd, HH:mm:ss`).
- **High-Contrast Stream Legibility:** Styled with matching `#EFEFFE` typography (`55px` clock, `69px` location) reinforced with multi-layer drop shadows for visibility against bright outdoor environments.
- **Fail-Safe Offline Mode:** Gracefully defaults to fallback coordinates (e.g., `Las Vegas, NV`) if GPS permission is denied or mobile data drops.

### 1. Adding or Modifying Major Metros
In the `MAJOR_METROS` JavaScript array, you can add or adjust anchor cities to fit your common travel routes:

```javascript
const MAJOR_METROS = [
  { name: "Los Angeles, CA", lat: 34.0522, lon: -118.2437 },
  { name: "Las Vegas, NV", lat: 36.1699, lon: -115.1398 },
  { name: "San Diego, CA", lat: 32.7157, lon: -117.1611 },
  { name: "San Francisco, CA", lat: 37.7749, lon: -122.4194 },
  { name: "Phoenix, AZ", lat: 33.4484, lon: -112.0740 },
  // Add custom anchors:
  { name: "Salt Lake City, UT", lat: 40.7608, lon: -111.8910 }
];
```

### 2. Switching to Celsius
If you prefer Celsius over Fahrenheit, adjust the Open-Meteo URL query parameter:

```javascript
// Change 'temperature_unit=fahrenheit' to 'temperature_unit=celsius'
`https://api.open-meteo.com/v1/forecast?latitude=${metro.lat}&longitude=${metro.lon}&current=temperature_2m,weather_code&temperature_unit=celsius`
```
And replace `°F` with `°C` in the DOM assignment:
```javascript
document.getElementById('location-weather').textContent = `${metro.name} • ${temp}°C ${icon}`;
```

### 3. Update Frequency
By default, the location and weather cycle runs every 10 minutes (`600000` ms). To change it (e.g., to 15 minutes):
```javascript
const UPDATE_INTERVAL = 15 * 60 * 1000; // 900,000 ms
setInterval(updateLocationAndWeather, UPDATE_INTERVAL);
```

---

## 🔒 Privacy & Safety Notice (OPSEC)

- **Network-Level Geolocation:** The script specifies `enableHighAccuracy: false` to force Android to rely on cell towers and Wi-Fi beacons rather than raw GPS satellite locks.
- **Anchor Snapping:** The user's exact coordinates are never printed to the screen, passed to any logging server, or stored in cookies. The coordinates are only evaluated against Euclidean/Haversine mathematical distances in browser memory.

---

## 📄 License

Proprietary / Source-Available for personal live broadcasting configurations.
