# Event Photos

Put your event photos in these folders:

- clubs/ — Club & disco event shots
- weddings/ — Weddings
- private/ — Private & corporate events

Recommended
- Use JPG or WebP. WebP gives smaller file sizes.
- Name files with a short slug and date, e.g. `berlin-club-2025-06-21-01.jpg`
- Resize to max width ~1920px; create a 1200px or 1600px version if originals are huge
- Optimize images before committing (e.g., Squoosh, TinyPNG)

How to reference in index.html

Example markup you can paste into the Events section (or create a new Photos section):

<!--
<section id="photos">
  <div class="container">
    <h2 class="section-title">Event Photos</h2>
    <div class="grid" style="grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 10px">
      <figure class="card" style="padding:0; overflow:hidden">
        <img src="assets/images/events/clubs/berlin-club-2025-06-21-01.jpg" alt="Club event photo — Berlin" style="display:block; width:100%; height:100%; object-fit:cover" loading="lazy" />
      </figure>
      <figure class="card" style="padding:0; overflow:hidden">
        <img src="assets/images/events/weddings/munich-wedding-2025-07-12-01.jpg" alt="Wedding photo — Munich" style="display:block; width:100%; height:100%; object-fit:cover" loading="lazy" />
      </figure>
    </div>
  </div>
</section>
-->

Tip: Keep alt text short but descriptive for accessibility and SEO.
