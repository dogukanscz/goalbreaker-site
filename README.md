# Goalbreaker website

The English-only website for Goalbreaker by Talvero Games. Static HTML and CSS on GitHub Pages; no build step, JavaScript, website analytics or third-party font requests.

## Public links

| Store field | URL |
| --- | --- |
| Website / Marketing URL | https://dogukanscz.github.io/goalbreaker-site/ |
| Privacy Policy URL | https://dogukanscz.github.io/goalbreaker-site/privacy.html |
| Support URL | https://dogukanscz.github.io/goalbreaker-site/support.html |

The game introduction lives on one landing page. Privacy and support have separate, stable URLs for store listings and existing app versions. `gizlilik.html` redirects to the English policy and retains a manual link for clients that do not follow the redirect. `404.html` uses the project base path so links also work from missing nested URLs.

## Editing and publishing

- Start a package branch from current `origin/main` (this **website repository** publishes from `main`; the separate Unity repository's frozen `main` is unrelated).
- Preview locally with `python3 -m http.server 8765 --bind 127.0.0.1`.
- Check desktop and mobile layouts, keyboard navigation, links, privacy anchors, redirect and publisher file before merging.
- Keep the effective date and `sitemap.xml` current when changing policy wording. Update the stylesheet version in all pages when changing CSS.
- Merge the verified package into this repository's `main` and push. GitHub Pages publishes the root directory. Keep the package branch for the work history.
- Keep real download links out until their public store destinations have been verified. The current landing page accurately says the game is in testing.
- Preserve `privacy.html`, `support.html`, the legacy `gizlilik.html` route and the AdMob publisher record.

`app-ads.txt` contains the existing AdMob publisher record. The domain-root copy at `https://dogukanscz.github.io/app-ads.txt` is served by the separate `dogukanscz.github.io` repository and must also remain available.

## Content and privacy facts

The 18 September 2026 copy was checked against the Unity project's `docs/DATA_INVENTORY.md`, `GameSettings`, `FirebaseAnalyticsService`, `AdMobAdService`, `AdConsent`, `SaveService` and English Settings labels. The first release has no IAP, no player accounts and no game-managed cloud save. Optional Firebase sharing is off by default. Advertising processing is separate and can begin while preloading, before a player watches an optional rewarded video.

Do not promise automatic recovery of progress, complete anonymity, no data processing before an ad is watched, or deletion of all provider data merely by uninstalling. The Analytics property's actual retention setting still needs verification in the service console; the policy deliberately does not claim the unconfirmed two-month target is configured. AdMob consent delivery and Play Data safety declarations require their own checks and are not certified by this website update.

Provider and policy references reviewed for the refresh:

- [Google Play User Data](https://support.google.com/googleplay/android-developer/answer/10144311?hl=en)
- [AdMob data disclosure](https://developers.google.com/admob/unity/privacy/play-data-disclosure)
- [AdMob consent integration](https://developers.google.com/admob/unity/privacy)
- [Firebase privacy and security](https://firebase.google.com/support/privacy)
- [European Commission privacy rights](https://commission.europa.eu/law/law-topic/data-protection/information-individuals_en)
- [California privacy rights](https://oag.ca.gov/privacy/ccpa)
- [GitHub Pages data collection](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages#data-collection)

## Assets and licences

- The logo, icon and social cover are the game's existing official art. `social-cover.png` is the English `art/store/feature_1024x500_en.png`.
- `home.webp` is the English `tools/out/release-ui/en-home.png` capture.
- `gameplay.webp` is `tools/out/level_review/2026-09-14/new_50_final/A02_opening.png`.
- `celebration.webp` is `tools/out/level_review/2026-09-14/new_50_baseline/A20_trace_end.png`.
- WebP captures are resized/compressed exports of real game captures, with no invented gameplay. Original assets remain intact in the game repository. The older `shot-title.jpg` is retained for existing links/history but is no longer displayed.
- Barlow Condensed (800) and Nunito Sans (variable weight) are served locally as Latin WOFF2 subsets from Google Fonts. Their SIL Open Font License files are included under `assets/fonts/`.

## Verification — 18 September 2026

- All five HTML documents pass `html-validate` recommended checks.
- Home, support and privacy checked at 320, 390, 768, 1024 and 1440 CSS pixels: no horizontal overflow, clipped text or missing images after scrolling.
- Six axe WCAG A/AA scans (390 and 1440 px across the three pages): zero violations reported. Automated scans do not replace a complete accessibility audit.
- Eight interaction checks pass: FAQ keyboard open/close, policy contents, skip link focus/navigation, legacy redirect, and FAQ/redirect with JavaScript disabled.
- 101 HTML resource/link references plus CSS font resources checked; no missing local targets or fragments. No page errors, failed asset requests or external asset requests during the browser run.
- Desktop and mobile screenshots reviewed. Browser: isolated headless Chrome 153.0.8010.50; no personal browser profile. Native Safari and physical-phone checks were not part of this run.
- Both live publisher records returned HTTP 200 with `pub-4171096744461223` before deployment; their contents are unchanged.
