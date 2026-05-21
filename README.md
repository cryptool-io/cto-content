# cto-content

Content source for the cryptool.io **Blog** and **News & Announcements**.

**One JSON file per post:**

```
blog/<slug>.json
news/<slug>.json
```

- The filename (without `.json`) must equal the post's `slug`.
- Schema (the contract): `cto-landing/scripts/posts.schema.json`.
- Full publishing instructions for AMT: `cto-landing/AMT-PUBLISHING-HANDOFF.md`.

## How it deploys

AMT (or a person) creates/updates a post file here, then sends a
`repository_dispatch` (`event_type: content-updated`) to the `cto-landing`
repo. `cto-landing` then validates this content, prerenders it to static HTML
(SEO), and deploys to AWS S3 + CloudFront automatically. A malformed post
fails the build and is **not** deployed — the live site stays up.

Do **not** put rendering, HTML templates, or build config here — this repo is
content only.
