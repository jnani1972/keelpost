# SEO checks

The checks the writer runs on every article (blog channel) before it is marked ready. Other channels skip this file.
How to use: keep the required checks; add your own below them. Each check needs a pass condition someone could test by reading the draft.

## Required checks

| id | check | passes when |
| --- | --- | --- |
| S-01 | keyword in title | the assigned keyword, or a close form of it, is in the title |
| S-02 | keyword early | the keyword appears in the first 100 words |
| S-03 | keyword in a subheading | at least one subheading contains the keyword |
| S-04 | meta description | present and 155 characters or fewer, including spaces |
| S-05 | one owning page | no other live URL in `brand/search/keywords.md` owns this keyword |
| S-06 | links | at least one link to another page of ours; no link to a competitor |
| S-07 | facts sourced | every number and claim is in `sources`, or carries `[CHECK]` |

## Owner's own checks

| id | check | passes when |
| --- | --- | --- |
| S-10 | {{fill: e.g. local area named}} | {{fill: e.g. the neighbourhood name appears once in the body}} |

## When a check fails

1. The writer fixes the draft and runs the check again, once.
2. If it still fails, the writer leaves the draft as is, lists the failed check in the front matter under `seo`, and says so in what it returns.
3. A failed S-05 goes back to the director: it means two pages may compete, and search-watch should look at it.
4. A failed S-07 means the draft carries `[CHECK]` and cannot auto-ship.

## Sample result (Harbor Lane Bikes, delete when done)

```yaml
seo:
  S-01: pass
  S-02: pass
  S-03: fail (no subheading has "winter bike maintenance")
  S-04: pass (142 characters)
  S-05: pass
  S-06: pass
  S-07: pass
```
