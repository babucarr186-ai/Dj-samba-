# Media uploads (no-code) with Supabase Storage

This site can show photo/video galleries and let you upload new media from the page without editing code or committing files.

## Quick setup (10–15 minutes)

1) Create a free Supabase project
- https://supabase.com/ → New project
- Note your Project URL and the anon public key

2) Create 3 public buckets
- In Storage → Create buckets named: `clubs`, `weddings`, `private`
- Visibility: Public (so the site can read without auth)

3) Copy the sample config
- Duplicate `assets/config.sample.json` → `assets/config.json`
- Fill in:
  - `supabaseUrl`: your Project URL
  - `supabaseAnonKey`: your anon public key
  - Buckets: keep names unless you changed them

Example:

```
{
  "storage": {
    "provider": "supabase",
    "supabaseUrl": "https://abcd1234.supabase.co",
    "supabaseAnonKey": "eyJhbGciOi...",
    "buckets": {
      "clubs": "clubs",
      "weddings": "weddings",
      "private": "private"
    }
  }
}
```

4) Deploy or run locally
- When `assets/config.json` is present, the Upload button appears in the Photos section
- The site will list existing files from each bucket and let you upload new ones

## Usage
- Use the tabs (Clubs/Weddings/Private) to pick a category
- Click "Upload media" and select images/videos (JPG/PNG/WebP/MP4/WEBM)
- Uploads are added instantly to the grid

## Tips
- Supabase Storage is public when buckets are public; don’t upload sensitive data
- Files are given unique names using a timestamp; original name is sanitized
- For best performance, upload images sized ≤ 1920px width (or use WebP)

## Troubleshooting
- Upload button not showing: ensure `assets/config.json` exists and is valid JSON
- No files listed: confirm bucket names and that they are set to Public
- CORS: Supabase handles CORS by default for Storage public assets

If you want to use another storage (Cloudinary, Uploadcare, S3), we can add an adapter later.
