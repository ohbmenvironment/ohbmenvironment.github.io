---
title: OHBM YYYY
permalink: /ohbm-YYYY/
---

To create a new event page, make a copy of this file and rename it. If the page is about the OHBM annual meeting or a satellite event, you can rename use the `ohbm-YYYY.md` format.

Then update the front matter (block at the top of this file) to have a new title and permalink.

Then add the page to the `_data/navigation.yml` file's `events` section. If the event is for a new year, create a new section for the year. Otherwise, add it as a child of an existing section. The `url` field must match the file's permalink. For example:
```yaml
  - title: YYYY
    children:
      - title: OHBM YYYY
        url: /ohbm-YYYY/
      - title: OHBM YYYY satellite event
        url: /ohbm-YYYY-satellite event
```
