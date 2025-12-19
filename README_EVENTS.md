# Upcoming Events Planner

Add a customer-friendly "Upcoming Events" section that you can manage without code.

## Two ways to manage events

- **JSON file (quick manual edits):**
  - Create `assets/events.json` following the sample structure.
  - The site reads this file and displays event cards automatically.

- **Airtable (no-code form + live view):**
  - Add `events` to `assets/config.json`:
    ```json
    {
      "events": {
        "provider": "airtable",
        "formUrl": "https://airtable.com/appXXXXXXXX/pagYYYYYYYY",
        "embedUrl": "https://airtable.com/embed/appXXXXXXXX/tblAAAAAA/viwBBBBBB"
      }
    }
    ```
  - The Upload/Submit button opens your form.
  - The grid embeds your Airtable view and updates as you add records.

## JSON structure

Use `assets/events.sample.json` as a template and create `assets/events.json`:

```json
{
  "events": [
    {
      "title": "New Year's Eve — Club XYZ",
      "date": "2025-12-31T22:00:00Z",
      "endDate": "2026-01-01T04:00:00Z",
      "venue": "Club XYZ",
      "city": "Berlin",
      "country": "DE",
      "link": "https://tickets.example.com/ny-xyz",
      "image": "assets/images/events/clubs/example.jpg"
    }
  ]
}
```

Fields:
- `title` — event name
- `date` — ISO start datetime (UTC recommended)
- `endDate` — optional ISO end datetime
- `venue`, `city`, `country` — location details
- `link` — ticket or info URL
- `image` — optional image path

## Calendar links

Each event card includes an "Add to calendar" button (Google Calendar link). If you provide `endDate`, the time range is set accordingly.

## Notes
- If `config.json` includes `events.provider = airtable`, the site switches to embed mode and uses your form.
- If `assets/events.json` is present and no Airtable provider is set, the site lists events from JSON.
- i18n: English and German texts are included for the planner section.
