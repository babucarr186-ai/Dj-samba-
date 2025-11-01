# Deejay Samba — One-Page Website

A fast, modern single-page site for Deejay Samba with inline CSS and native audio previews.

## Structure

- `index.html` — main page (no frameworks)
- `assets/images/` — place hero/background images (e.g., `dj-hero.jpg`)
- `assets/audio/` — place short MP3 clips for each category

## Replace assets

- Hero background: add an image at `assets/images/dj-hero.jpg` (recommended 1920×1080 or larger). The page will fallback to a royalty-free Unsplash photo if the local file is missing.
- Audio previews: add MP3 files using these exact names (or update paths in the HTML):
  - `afrobeats-1.mp3`, `afrobeats-2.mp3`
  - `amapiano-1.mp3`, `amapiano-2.mp3`
  - `hiphop-1.mp3`, `hiphop-2.mp3`
  - `latin-1.mp3`, `latin-2.mp3`
  - `live-mix-1.mp3`, `live-mix-2.mp3`

If MP3s are missing, the site auto-generates short WAV demo loops so audio players always work during development.

## Booking form

The form uses `mailto:` to send to `bookings@deejaysamba.com`. This opens the visitor's default email app. For a production-ready form with server-side handling, connect a service like Formspree, Basin, or a custom API and update the form `action` accordingly.

## Preview locally (Windows)

You can open the file directly in your browser:

```powershell
# In the project folder
start .\index.html
```

Or run a simple local server (optional if you have Python installed):

```powershell
# Python 3
python -m http.server 5500 ; start http://localhost:5500/index.html
```

## Customize

- Colors and spacing live in CSS variables at the top of `index.html`.
- Update the call number in the Booking section (`tel:+12025550147`).

## License

All placeholder code is MIT. Replace assets with media you own or that is licensed for your use.
