# Deejay Samba — One-Page Website

A fast, modern single-page site for Deejay Samba with inline CSS and native audio previews.

## Structure

- `index.html` — main page (no frameworks)
- `assets/images/` — place hero/background images (e.g., `dj-hero.jpg`)
- `assets/audio/` — optional: if you want, place your own audio files; otherwise the site generates short demo loops

## Replace assets

- Hero background: add an image at `assets/images/dj-hero.jpg` (recommended 1920×1080 or larger). The page will fallback to a royalty-free Unsplash photo if the local file is missing.
Audio previews: by default, the site auto-generates short WAV demo loops for each genre (Afrobeats, Amapiano, Hip‑Hop, Latin, Mix). This keeps things lightweight and avoids shipping MP3s.
If you prefer to use your own tracks, embed Spotify or SoundCloud players (there are placeholders in `index.html`).

## Booking form

The form posts to FormSubmit and emails `ngumjoh@gmail.com` directly (no mailto needed). It uses a honeypot for basic spam protection and redirects to a Thank You state.
If you switch providers later, just update the form `action` and hidden fields in `index.html`.

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
- Update the call number in the Booking section (`tel:+4917662350091`).

## License

All placeholder code is MIT. Replace assets with media you own or that is licensed for your use.
