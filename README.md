
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
