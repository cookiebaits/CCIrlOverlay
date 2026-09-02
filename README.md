# CookieClip IRL Overlay - https://github.com/cookiebaits/CCIrlOverlay 

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

---

## 📁 File Structure

```text
├── index.html        # Standalone overlay interface (HTML, CSS, JS)
└── README.md         # Documentation & deployment instructions
