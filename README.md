# pf-media

Public media host for [Prompt Frontier](https://instagram.com/promptfrontier) renders.

## Why this exists

Instagram's Content Publishing API has no file upload — Meta **pulls** the video from a public
HTTPS URL. So every render has to be world-readable before Instagram will accept it. This repo
is that URL, and nothing else.

Videos live under `v/` and are served by GitHub Pages at:

```
https://allevic.github.io/pf-media/v/<name>.mp4
```

## Why Pages and not raw.githubusercontent.com

`raw.githubusercontent.com` serves `.mp4` as `Content-Type: application/octet-stream`, which
Meta's ingestion rejects. GitHub Pages serves the same file as `video/mp4`. Both were checked
directly — this is the only reason the repo has a Pages site rather than just files.

## Housekeeping

Git keeps every version of every binary forever, so at ~14 MB/render this grows about **5 GB
per year** and deleting files reclaims nothing. GitHub recommends staying under 1 GB and warns
at 5 GB.

When it gets fat, don't prune — **delete this repo and recreate it**. Nothing here is a source
of truth: the compositions, prompts, and provenance live in the main project, and Meta re-hosts
each video on its own CDN once a post goes out. These files are disposable the moment Instagram
has ingested them.

If the daily cadence sticks, move to object storage (Cloudflare R2's free tier has zero egress
fees and no history to bloat) and retire this.
