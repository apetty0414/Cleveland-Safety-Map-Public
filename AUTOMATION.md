# Automatic Registry Refresh

## What this framework does

The repository now contains a scheduled GitHub Actions pipeline that can:

1. Read an approved JSON registry feed.
2. Normalize fields.
3. Remove duplicates.
4. Geocode only records that do not already contain coordinates.
5. Cache geocoding results.
6. Validate output.
7. Track new/changed/removed-source records.
8. Update `registry-data.json`.
9. Commit changes back to the repository.
10. Trigger GitHub Pages redeployment automatically.

## What it intentionally does NOT do

It does **not** scrape Ohio eSORN HTML pages or reverse-engineer private/internal APIs.

Before enabling automatic refresh, configure a permitted/public source.

## GitHub configuration

Repository → Settings → Secrets and variables → Actions

### Secret
`REGISTRY_SOURCE_URL`
- URL of the approved JSON feed or your own data endpoint.

Optional secret:
`REGISTRY_SOURCE_AUTH_HEADER`
- Full Authorization header value if your approved endpoint requires it.

### Variable
`REGISTRY_SOURCE_LABEL`
- Friendly source label, for example `Ohio approved feed`.

## Manual test

Actions → Refresh Registry Data → Run workflow

If successful, the action updates:
- `registry-data.json`
- `registry-changes.json`
- `data/geocode-cache.json`

## Schedule

The workflow currently runs daily at `09:17 UTC`.
GitHub scheduled workflows are not guaranteed to start at the exact minute.

## Local testing

```bash
python -m pip install -r requirements.txt
export REGISTRY_ADAPTER=local_file
export REGISTRY_LOCAL_FILE=seed-source.json
python scripts/fetch_registry.py
python scripts/smoke_test.py
```

## Expected source fields

The normalizer accepts common aliases, but the ideal JSON record is:

```json
{
  "id": "public-registry-id",
  "name": "Example Name",
  "address": "123 Main St, Cleveland, OH 44111",
  "classification": "Tier II",
  "offense": "Example published offense",
  "minorRelated": true,
  "profile": "https://example.gov/profile/123",
  "lat": 41.0,
  "lon": -81.0
}
```

Coordinates are preferred because they avoid geocoding overhead.
