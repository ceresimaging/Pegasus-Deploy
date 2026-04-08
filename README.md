<p align="center">
  <img src="assets/logo.webp" alt="Pegasus" width="300">
</p>

<h1 align="center">Pegasus Deploy</h1>

<p align="center">
  Enterprise iOS distribution for the Pegasus flight navigation app.<br>
  <a href="https://ceresimaging.github.io/Pegasus-Deploy/">Install Pegasus</a>
</p>

---

## What is Pegasus?

Pegasus is an iOS app used by agricultural pilots to navigate precision aerial imaging flights. It provides real-time GPS tracking, field pass guidance, BLE camera system integration, and flight planning tools.

## Installing Pegasus

Open the install page on your iOS device in **Safari**:

**https://ceresimaging.github.io/Pegasus-Deploy/**

After installing, trust the developer certificate:
1. Go to **Settings > General > VPN & Device Management**
2. Tap **Ceres Imaging, Inc.**
3. Tap **Trust**

## Updating the App

1. Export a new `.ipa` from Xcode (Distribute App > Enterprise)
2. Replace `Pegasus.ipa` in the repo root
3. Update `manifest.plist` if the version number changed
4. If adding a new version, create a JSON file in `releases/` and add it to `releases/index.json`
5. Commit and push

## Adding Release Notes

Drop a new JSON file in `releases/`:

```json
{
  "version": "2.1.0.1",
  "date": "2025-09-03",
  "notes": [
    "First change",
    "Second change"
  ]
}
```

Then add the filename to `releases/index.json`. The website loads these dynamically.

## Repo Structure

```
Pegasus.ipa          # The app binary (not checked into git, use Git LFS if needed)
manifest.plist       # iOS OTA install manifest
index.html           # Install page (hosted via GitHub Pages)
assets/              # Logo, animation
releases/            # Individual JSON files per version (loaded dynamically)
  index.json         # Manifest listing all release JSON filenames
  2.1.0.0.json
  2.0.4.9.json
  ...
```

## Local Development

To preview locally (fetch won't work with file:// URLs):

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```
