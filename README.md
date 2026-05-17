# TollGuru India 🚗

Live toll calculator and route planner for India — built with pure HTML/CSS/JS, no backend required.

## Files

```
tollguru/
├── index.html      ← Main calculator (home page)
├── dashboard.html  ← User trip history & stats
├── admin.html      ← Admin panel (admin@tollguru.com only)
├── vercel.json     ← Vercel deployment config
└── README.md
```

## Deploy to Vercel (15 minutes)

### Step 1 — Push to GitHub
1. Create a new repo at https://github.com/new (name it `tollguru-india`)
2. Upload all 4 files (index, dashboard, admin, vercel.json)

### Step 2 — Deploy on Vercel
1. Go to https://vercel.com and log in with GitHub
2. Click **Add New Project** → select your repo
3. Leave all settings as default → click **Deploy**
4. You'll get a live URL like `https://tollguru-india.vercel.app`

### Step 3 — Custom Domain (optional)
- In Vercel project → **Settings → Domains**
- Add your domain (e.g. `tollguruindia.in` from Namecheap)
- Update DNS as instructed by Vercel

## Demo Credentials

| Role  | Email                   | Password |
|-------|-------------------------|----------|
| User  | anyemail@example.com    | demo123  |
| Admin | admin@tollguru.com      | demo123  |

## APIs Used (all free, no key needed)

| Service | Purpose |
|---------|---------|
| Nominatim (OSM) | City geocoding |
| OSRM | Driving route calculation |
| Carto Tiles | Map tiles |
| @mapbox/polyline | Decode OSRM route geometry |

## Bug Fixes Applied

1. **Broken template literals** — All JS string concatenation fixed
2. **Missing polyline decoder** — Added `@mapbox/polyline` CDN script; OSRM returns encoded polyline that base Leaflet can't decode
3. **CORS error on Nominatim** — Removed `User-Agent` header (browsers block custom headers with Nominatim CORS policy)
4. **Map instance leak** — `mapInstance.remove()` called before re-render to prevent "Map container already initialized" error
5. **Trip storage cap** — Capped at 50 trips per user to prevent localStorage overflow

## Tech Stack

- Frontend: HTML5, CSS3, Vanilla JS
- Maps: Leaflet.js + Carto tiles
- Routing: OSRM (free public API)
- Geocoding: Nominatim (OpenStreetMap)
- Auth: localStorage (demo — upgrade to Firebase for production)
- Deployment: Vercel

## Roadmap (Next Steps)

- [ ] Firebase Auth + Firestore (replace localStorage)
- [ ] FASTag cost estimation
- [ ] Live fuel price API
- [ ] Route alternatives (fastest / cheapest / toll-free)
- [ ] PDF trip export
- [ ] PWA / offline support
