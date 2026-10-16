# Roadblock & Weather Disruption Ops Command

## Deploy on GitHub Pages
1. Create a new GitHub repository (Public is simplest for GitHub Pages on the free plan).
2. Upload `index.html` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/(root)`, then click **Save**.
6. Wait for the Pages deployment to finish; open the URL shown under **Settings → Pages**.
7. Test in a private/incognito window and on a second device.

## Important product limitations before production
- This is a static front-end prototype. Published updates are stored in the current browser's `localStorage`; they do **not** automatically sync between different agents, computers, or browsers.
- The admin passcode is a front-end demonstration gate (`2468`) and is visible in client-side source. It is **not secure authentication**. Do not publish sensitive operational data or rely on this gate to restrict access.
- For real multi-user live publishing, add a backend (for example Supabase or a small API) with server-side authentication, row-level access rules, and a shared database. Configure secrets only in the backend, never in `index.html`.
- The interactive map loads Leaflet from a public CDN and district GeoJSON from public URLs. No API key is required, but an internet connection is needed for these resources. If those public endpoints change or become unavailable, the map may not load.
- The page is one HTML file and does not need a build step. The map and city image assets currently use external URLs.

## Quick smoke test
- Open the site; confirm the map reports district boundaries loaded (internet required).
- Click **Command Center**: the agent dashboard should disappear and the admin login should occupy the viewport immediately below the header.
- Use demo passcode `2468` only for local testing; unlock, create a test update, and publish.
- Return to **Agent view** and verify the update appears in the city directory, recent updates, mini dashboard, and map marker (if the city is in the configured coordinate list).
- Test on mobile width and refresh the page.
- Delete test records before using the prototype for a demonstration.
