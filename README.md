# Regional Family Safety Map — Public-Safe PWA

This version expands the original neighborhood map into a regional/general-purpose tool.

## Key improvements
- Adjustable radius from **1 to 50 miles**
- Quick presets: 1, 5, 10, 25, and 50 miles
- Any private reference location can be entered on-device
- Multiple reference locations can be saved locally (Home, School, Grandparents, etc.)
- Browse/recenter the map anywhere without changing the private reference
- 1/5/10-mile guide rings plus selected-radius ring
- Distance and nearest-first filtering around the selected reference
- Local CSV/JSON registry import, stored in browser only
- Apple Maps and Google Maps links
- Installable PWA on iPhone/Android
- No private home address or coordinates stored in GitHub

## Important data-coverage note
The built-in dataset still contains only the original Cleveland-area sample. Increasing the radius does **not** automatically retrieve additional registry entries.

For use in other areas, import a CSV/JSON dataset locally or use the official registry search for that jurisdiction.

## CSV format
`name,address,classification,offense,minorRelated,profile`

The app will geocode imported addresses in the user's browser and cache the results locally.

## GitHub Pages
Upload all files to a public repository root, then:
Settings → Pages → Deploy from a branch → `main` → `/ (root)`.

## Privacy
Private reference locations and imported datasets are stored in browser localStorage only and are not committed to GitHub.


## Automatic data refresh

This package includes a GitHub Actions automation framework under:

`.github/workflows/refresh-registry.yml`

See `AUTOMATION.md` for setup. The automation expects an approved/public JSON feed configured through GitHub Secrets. It intentionally does not scrape registry web pages.
