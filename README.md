# finlab-carousel

Private assets + instructions for the FinLab Instagram carousel generator (Cloud Routine reads
from this repo). Not public — personal photos live here.

## Structure

- `finlab_carousel_generator.md` — the design-system instructions (source of truth for style,
  copy rules, layout variety, export).
- `carousel-assets/profile-olesya.jpg` — profile photo for callout headers.
- `carousel-assets/photos/` — content photos for slides. **Olesya refills this in batches.**
  Drop images here; the generator picks from whatever is available. Fewer photos than slides
  is fine — the rest become clean text-only slides.

## How the automated flow uses it

1. Telegram message with a topic → small Supabase forwarder → Cloud Routine API trigger.
2. The Cloud Routine reads `finlab_carousel_generator.md` and the photos in `carousel-assets/`,
   writes the copy, builds the HTML, exports 1080×1350 PNGs, and sends them back to Telegram.

## Adding photos

- Web: **Add file → Upload files**, drag images into `carousel-assets/photos/`, commit.
- Local: drop files into `carousel-assets/photos/`, then `git add`, `git commit`, `git push`.
