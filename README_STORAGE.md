# Media uploads (no-code)

This site supports two convenient, no-code options for adding photos/videos without committing files.

## Option A: Supabase Storage (direct uploads)

Best if you want uploads directly on the page and your own storage/CDN.

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
- When `assets/config.json` is present and valid, the Upload button appears in the Photos section
- The site will list existing files from each bucket and let you upload new ones

## Option B: Airtable (form uploads + embedded galleries)

Easiest for non-technical users. People upload via an Airtable Form; galleries on the site show embedded Airtable views that auto‑update.

1) Create a free Airtable account and a base
- Table: `Event Photos`
- Fields:
  - `Attachment` (type: Attachment, allow multiple)
  - `Category` (type: Single select: Clubs, Weddings, Private)
  - Optional: `Caption`, `Photographer`, etc.

2) Create three filtered views (or three separate views)
- View: `Clubs` (filter Category = Clubs)
- View: `Weddings` (filter Category = Weddings)
- View: `Private` (filter Category = Private)
- For each view: Share and copy the “Embed this view” URL

3) Create a Form view for uploads
- Include `Attachment` and `Category` (required)
- Copy the Form share URL. You can prefill the category using `prefill_Category=Clubs` etc.

4) Add the Airtable config file
- Copy `assets/config.airtable.sample.json` → `assets/config.json`
- Fill in:
  - `formUrl`: your Form URL; include `prefill_Category={category}` to auto‑fill based on the active tab
  - `embedUrls.clubs|weddings|private`: the three embed URLs from step 2

Example:

```
{
  "storage": {
    "provider": "airtable",
    "formUrl": "https://airtable.com/appXXXXXXXXXXXXXX/pagYYYYYYYYYYYY?prefill_Category={category}",
    "embedUrls": {
      "clubs": "https://airtable.com/embed/appXXXXXXXXXXXXXX/tblAAAAAAAAAAAA/viwCCCCCCCCCCCC?viewControls=on",
      "weddings": "https://airtable.com/embed/appXXXXXXXXXXXXXX/tblBBBBBBBBBBBB/viwDDDDDDDDDDDD?viewControls=on",
      "private": "https://airtable.com/embed/appXXXXXXXXXXXXXX/tblEEEEEEEEEEEE/viwFFFFFFFFFFFF?viewControls=on"
    }
  }
}
```

5) Deploy
- The Photos tab will render each view in an embedded iframe
- The “Upload media” button opens your Airtable form with the tab’s category pre‑selected

### Notes
- Airtable embeds work publicly if your shared view is public
- To prevent spam, you can enable CAPTCHA on the form (Airtable setting)
- For a custom look, you can style views in Airtable or switch to Supabase later

## Troubleshooting
- Upload button not showing: ensure `assets/config.json` exists and choose either provider
- Supabase path: verify URL looks like `https://*.supabase.co` and anon key starts with `eyJ` and is long
- Airtable path: confirm `embedUrls` are valid “Embed this view” links and `formUrl` opens

If you prefer another storage (Cloudinary, Uploadcare, S3), we can add an adapter later.
