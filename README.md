# CookieClip IRL Overlay - 
https://cookiebaits.github.io/CCIrlOverlay/ 

A lightweight, battery-efficient, client-side browser overlay engineered for the **IRL Pro** Android live streaming app and OBS / PRISM Live Studio.

It automates location display with built-in **OPSEC / privacy protection**, snapping your coarse GPS position to the nearest major metropolitan area (e.g., Beverly Hills, Santa Monica, or Glendale displays as **"Los Angeles"**), alongside real-time temperature and weather icons updated every 10 minutes displayed side-by-side with the date and time on the bottom row.

---

## 🌟 Features

- **Coarse Geo-Fencing & OPSEC:** Snaps approximate GPS coordinates to predefined anchor metropolitan hubs using great-circle haversine calculation. Never leaks precise streets, venues, or suburban neighborhoods on stream.
- **Zero API Keys Required:** Integrates with [Open-Meteo](https://open-meteo.com/) for real-time weather code mappings and Celsius / Fahrenheit temperatures (defaults to Celsius; configurable via `?unit=F`).
- **Ultra-Low Battery & Data Footprint:** Requests coarse network location (`enableHighAccuracy: false`) with a 10-minute caching lifecycle (`maximumAge: 600000`) and a 10-minute poll interval (`600,000 ms`).
- **Side-by-Side Bottom Row Display:** Clean, compact bottom row layout presenting weather icon, temperature, city name, condition description, and date/time side-by-side.
- **Live Accurate Clock:** Smooth 1-second interval timestamp formatted with uppercase day, date, month, year, and 12-hour clock (e.g., `THU, 05 NOV 2026, 02:12 PM`).
- **High-Contrast Stream Legibility:** Styled with crisp typography and reinforced drop shadows for visibility against both bright and dark outdoor environments without obscuring bottom screen real estate.
- **Fail-Safe Offline Mode:** Gracefully defaults to fallback coordinates if GPS permission is denied or mobile data drops.

---

## 📁 File Structure

```text
├── index.html        # Standalone overlay interface (HTML, CSS, JS)
└── README.md         # Documentation & deployment instructions
```
