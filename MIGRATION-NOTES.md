# Migration notes — Draw! Tumblr blog → Jekyll

Source: the Draw! Tumblr blog (2011–2012). The original domain `blog.drawbang.com`
no longer resolves. The live blog is reachable at
https://drawbang-blog.tumblr.com/ (also https://www.tumblr.com/drawbang-blog);
it was checked on 2026-10-06 and contains the **identical 22-post set** as the
Wayback captures — no extra or newer posts. The migration was built from the
Wayback Machine captures (March/April 2016) since content is byte-identical and
the 2016 captures preserve the original reblog attribution (some source blogs
have since been deactivated/renamed).

## What was recovered

- **22 of 22 posts** (Nov 4, 2011 → Nov 30, 2012). Note: earlier estimates said
  "21 posts"; the archive actually lists 22. Nothing was skipped.
- Post types: 12 text posts, 5 photo posts (pixel-art GIFs/PNGs), 4 video posts
  (YouTube embeds), 1 link post, 4 reblogs with attribution preserved
  (maxcapacity, arsenalvisual, chungkingmansions ×2, benbrown).
- All tags preserved (e.g. #pixel art, #gif, #8bit, #development).
- **27 images** downloaded to `site/assets/img/<post-slug>/` and rewritten to
  local links. 8 of them were NOT in the Wayback Machine and were recovered
  from the still-live original hosts (`media.tumblr.com`, `pbs.twimg.com`).
- 4 YouTube embeds kept as privacy-friendly `youtube-nocookie` iframes
  (video IDs: VXXhDqfO4qA, iO94sUJoG1s, CT8t_1JXWn8, uqk4I1q0JK4).
- The link post ("Giovanni Cappellotto: Draw! future features") points to
  `http://potomak.tumblr.com/post/9160456126/draw-future-features` (original
  target; that blog is now deactivated — link kept for provenance).

## What was missing / broken / substituted

- **Nothing unrecoverable.** All 22 posts, all images, all embeds recovered.
- Post dates: Tumblr only shows the day, not the time. Times were synthesized
  (09:41 +1h per same-day post) purely to preserve chronological order within a
  day (verified against Tumblr's chronological post IDs).
- 10 posts had no title on Tumblr; titles were derived from captions/slugs and
  marked in `scratch/convert.py` (`TITLE_OVERRIDES`). Reblog posts are titled
  "… — via <source>".
- The two Nov 16, 2011 video posts shared one Tumblr slug
  (`the-making-of-new-drawbang-animation-feature`); Jekyll filenames were
  disambiguated as `…-part-1` / `…-part-2`.
- External links rewritten from `web.archive.org` wrappers and `t.umblr.com`
  redirect wrappers back to their original URLs. Some targets are dead
  (drawbang.com, reddit.drawbang.com, deactivated Tumblrs) — kept as-is for
  historical accuracy.
- Notes/likes counts were not migrated (not meaningful content).

## Image inventory

| Post | Images |
|---|---|
| draw-iphone-app | 3 PNG (twimg) |
| facebook-open-graph-custom-action-and-object | 2 PNG (twimg) |
| arsenalvisual-this-is-life-aquatic-by-daniel | 1 GIF (tumblr) |
| floppy-disk-evolution | 3 PNG + 1 GIF (draw.heroku.com S3) |
| forking-and-use-as-twitter-profile-image | 9 PNG (imgur) |
| maxcapacity-frog-by-max-capacity | 1 GIF (tumblr, recovered live) |
| working-on-draw-for-iphone | 2 PNG (pbs.twimg.com, recovered live) |
| mocking-up-new-isometric-interface | 1 PNG (tumblr, recovered live) |
| chungkingmansions-the-nes-color-palette | 1 PNG (tumblr, recovered live) |
| chungkingmansions-via-drawbang | 1 GIF (tumblr, recovered live) |
| benbrown-something-new-wow-cant-wait-to-see | 1 PNG (tumblr, recovered live) |
| new-interface-new-mood-new-pixel-season | 1 PNG (tumblr, recovered live) |

## Build

- `jekyll build` (Jekyll 4.4.1, no theme/plugins — hand-rolled minimal layouts)
  succeeds: 22 post pages, index, `/archive/`, `/tags/`, all 27 images copied.
- Pixel-art images get `image-rendering: pixelated` so GIFs stay crisp.

## Open decisions for the owner

1. **GitHub repo location**: which org/user + repo name should host this?
   (Suggested: a `drawbang/blog` repo publishing from `site/` or repo root.)
2. **Custom domain vs github.io**: keep a `blog.drawbang.com`-style custom
   domain (needs DNS CNAME + `CNAME` file) or serve from
   `<user>.github.io/<repo>` (needs `baseurl` set in `_config.yml`)?
3. **Comments**: the old blog had none migrated; enable/disable (e.g. Giscus,
   Utterances) or leave static?
4. **Analytics**: add or skip?
5. **The dead link post target** (`potomak.tumblr.com/...`): try to recover that
   post's content from Wayback as a follow-up, or leave the link as-is?
6. **Asset URLs**: images currently served relative (`/assets/img/...`) — fine
   for custom domain; confirm `baseurl` if going the project-pages route.
