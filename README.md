# Family Safety Map — Public-Safe Build

This build is designed for public static hosting such as GitHub Pages.

## Privacy model

This repository contains **no private home address and no private home coordinates**.

The application asks the user to enter a private reference address or place on their own device. That reference point is geocoded in the browser and stored only in browser `localStorage`.

Because the reference location is not committed to GitHub, a public repository does not expose it.

Clearing browser/site data will remove the saved private reference point.

## GitHub Pages deployment

1. Create a new **public** GitHub repository, for example `Cleveland-Safety-Map`.
2. Upload every file from this folder to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and `/ (root)`.
6. Save.
7. Open the HTTPS URL GitHub provides.

## iPhone

Open the GitHub Pages HTTPS URL in Safari or Chrome.

In Safari:
Share → **Add to Home Screen**

The first time the app opens, enter your private reference location. It remains on that browser/device.

## Public-record data

The repository contains registry-derived candidate addresses and public family-location references used by the map. Registry information can change and should be verified against the official Ohio eSORN/Cuyahoga County registry before relying on it.

Do not use classification as an individualized danger score.
