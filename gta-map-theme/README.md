# GTA Map Theme for Google Maps

Makes Google Maps look like the GTA V map. Google Maps has no real "texture pack"
support, so there are two options:

## 1. GTA map page (best match)

`index.html` uses the Google Maps JavaScript API and recolors every map feature:

- **Pause-map style** (`pause-map-style.json`): olive land, navy water, dark green parks, light roads, no business icons.
- **Radar minimap** (`radar-style.json`) in the bottom left, with health, armor and ability bars.
- Character blips (M / F / T / $), a purple waypoint on right-click, money and wanted stars (press **W**), and the street and district name in the bottom right.
- Starts over Los Angeles (Los Santos).

### Run it

1. Get a Maps JavaScript API key from the Google Cloud console. Turn on the **Geocoding API** too if you want street and district names.
2. Serve this folder: `python3 -m http.server 8000`
3. Open `http://localhost:8000/index.html?key=YOUR_API_KEY`

### Install it as an app on your homescreen

The page is an installable web app. It has to be served over https, for example with GitHub Pages:

1. On GitHub, open the repo's **Settings → Pages**, choose **Deploy from a branch**, pick the
   branch with this folder and `/ (root)`, and save. (On a free plan the repo must be public.)
2. After a minute it's live at `https://<your-username>.github.io/<repo>/gta-map-theme/`.
3. In the Google Cloud console, restrict your API key to that address (HTTP referrers).
4. Open the address on your device and enter your API key once. It's saved on that device.
5. Add it to your homescreen:
   - **iPhone/iPad (Safari):** Share → **Add to Home Screen**
   - **Android (Chrome):** ⋮ menu → **Add to Home screen** / **Install app**
   - **Windows/Mac (Chrome or Edge):** the install icon at the right end of the address bar

It opens full screen with its own icon, like a normal app.

You can also paste `pause-map-style.json` into any project that takes Google Maps
JSON styles (`new google.maps.Map(el, { styles: [...] })`, or sites such as Snazzy Maps).
JSON styles don't apply to maps created with a `mapId`.

## 2. Browser extension for google.com/maps

`extension/` reskins the normal Google Maps site with a dark GTA-style filter.
google.com/maps draws the map on a canvas, so the extension can only change the
whole picture at once, not each feature. It's a rougher match than option 1.

Install in Chrome or Edge: open `chrome://extensions`, turn on **Developer mode**,
click **Load unpacked** and pick the `extension` folder. Change the `filter` line
in `extension/gta.css` to adjust the look.

## Font

The HUD uses Pricedown (the GTA font) if it's installed on your computer, and
falls back to Oswald otherwise.
