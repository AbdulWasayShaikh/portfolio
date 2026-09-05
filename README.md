# Portfolio

My personal site. **Live at [abdul-wasay-shaikh.netlify.app](https://abdul-wasay-shaikh.netlify.app)**

A single hand-written `index.html` with the CSS and JavaScript inline. No framework, no
build step, no page builder — clone it and serve the folder and that is the whole site.

## The hero

The hero video is fetched as a blob and scrubbed frame by frame against scroll position,
with four text bands composited over it. It only starts loading once the hero is engaged,
so a check run at page load will see `readyState 0` and think the video is broken when it
is not.

Phones, coarse pointers and anyone whose device asks for reduced motion get a still
(`assets/hero-ending.jpg`) instead, gated behind media queries — the scroll bands are
`display: none` there. The page never ships motion to someone who asked not to receive it.

## Legibility

White text over moving footage is a contrast problem that changes frame to frame, so the
bands were measured rather than eyeballed. The worst band reads **4.93:1** at 1440×900,
against the 4.5:1 WCAG AA target for normal text.

## Running it locally

There is no build step, but you do need a real HTTP server — opening the file directly
from disk will not work, because the hero video is loaded with `fetch()` and that is
blocked on `file://`.

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Layout

```
index.html        the entire site
assets/           hero video, poster and still, section and project images
```
