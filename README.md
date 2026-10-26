# Bus Route Visualizer — GitHub Pages site

A static, self-contained copy of the bus route visualizer plus one shipped
dataset. No API access, no credentials — just `index.html` and
`data/route.json`.

## Updating the shipped data

1. Open the local viewer (served from the parent project directory).
2. Use the **Data range** sliders to trim to the run you want to publish.
3. Click **Save…** — it downloads `route_YYYY-MM-DD.json`.
4. Replace `data/route.json` with that file:

   ```sh
   mv ~/Downloads/route_*.json data/route.json
   git add data/route.json && git commit -m "Update route data" && git push
   ```

The page auto-loads `data/route.json` on open; visitors can still drop their
own HAR/JSON file onto it.

## Updating the viewer

The viewer here is a copy of `../index.html`. After changing the original:

```sh
cp ../index.html index.html
git add index.html && git commit -m "Update viewer" && git push
```

## Enabling GitHub Pages

Settings → Pages → Deploy from a branch → `main` / `/ (root)`, or:

```sh
gh api repos/{owner}/{repo}/pages -f "source[branch]=main" -f "source[path]=/"
```

> **Privacy note:** `data/route.json` contains timestamped GPS fixes and
> street addresses along the route. Only make the repo public once you're
> comfortable publishing the dataset it currently holds.
