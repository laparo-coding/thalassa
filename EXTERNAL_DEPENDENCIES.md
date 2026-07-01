# External Dependencies

## Fonts (Google Fonts)

The HTML pages in this repository currently use externally hosted fonts from Google Fonts:

- CSS endpoint: `https://fonts.googleapis.com`
- Font files: `https://fonts.gstatic.com`
- Families: Inter, Playfair Display
- Referenced from:
  - `video-analysis.html`
  - `vorstellung-andreas.html`
  - `vorstellung-projekt.html`

## Risk

Using third-party font hosting introduces availability and privacy risk:

- Page rendering can degrade if Google Fonts is blocked or unavailable.
- Client requests to third-party domains may expose user metadata.

## Current Mitigation

A Content Security Policy (CSP) meta tag has been added to each HTML file to restrict and explicitly scope allowed sources for fonts, styles, and scripts. **Note:** CSP restricts *where* assets can load from but does not remove the Google Fonts runtime dependency—the HTML files still fetch font CSS and files from Google Fonts CDN (fonts.googleapis.com and fonts.gstatic.com).

## Decision: Retain Google Fonts

Google Fonts is retained as the font source due to:

- **Reliability**: Google Fonts CDN is highly available globally with strong SLA.
- **Maintenance**: No need to manage font file updates, versioning, or distribution.
- **Performance**: Widely cached by browsers across multiple sites.
- **Simplicity**: Minimal operational overhead compared to self-hosting.

### Trade-offs Accepted

- External runtime dependency on `https://fonts.googleapis.com` and `https://fonts.gstatic.com`.
- Minor privacy consideration: Google receives font requests.

### Mitigation in Place

Content Security Policy (CSP) is configured to:
- Explicitly whitelist Google Font domains.
- Restrict other external asset sources.
- Allow monitoring of unintended external loads.

This approach balances availability, maintainability, and acceptable risk for current project scope.
