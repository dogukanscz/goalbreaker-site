# Talvero Games website

The English-only website of Talvero Games at https://talverogames.com: the studio home page and the Goalbreaker pages. Static HTML and CSS on GitHub Pages with a custom domain; no build step, website analytics or third-party font requests. JavaScript appears only in the one-line forwards of the old addresses; the home page carries JSON-LD structured data.

## Addresses

| Use | URL |
| --- | --- |
| Studio home; Play "Website" field | https://talverogames.com/ |
| Goalbreaker | https://talverogames.com/goalbreaker/ |
| Privacy policy | https://talverogames.com/goalbreaker/privacy/ |
| Support | https://talverogames.com/goalbreaker/support/ |
| AdMob publisher record | https://talverogames.com/app-ads.txt |

`privacy.html`, `gizlilik.html` and `support.html` at the root forward to the new pages and keep the `#fragment` (meta refresh plus `location.replace`, both relative so they also work on the github.io project address). Released game versions open `https://dogukanscz.github.io/goalbreaker-site/privacy.html` and `.../gizlilik.html`. GitHub forwards that project address to `https://talverogames.com/<same path>` as long as the custom domain is set, and the root files then forward again. Keep all three files and the section ids of the policy.

`404.html` serves every missing path of the domain, so its links and assets use root paths (`/...`).

## Domain

- `CNAME` holds `talverogames.com`; Pages publishes `main` from the root (branch build).
- Cloudflare DNS, every record **DNS only** (grey cloud) so GitHub can issue the certificate:
  - four `A` records on `@`: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`;
  - four `AAAA` records on `@`: `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`;
  - `CNAME` `www` to `dogukanscz.github.io` (GitHub forwards `www` to the bare domain).
- "Enforce HTTPS" is turned on once GitHub has issued the certificate.
- `app-ads.txt` must stay at the domain root. The older copy at `https://dogukanscz.github.io/app-ads.txt` comes from the separate `dogukanscz.github.io` repository and stays while any listing still points at github.io.

## Editing and publishing

- Start a package branch from current `origin/main` (this **website repository** publishes from `main`; the separate Unity repository's frozen `main` is unrelated).
- Edit the HTML directly. Preview locally from the repository root with `python3 -m http.server 8765 --bind 127.0.0.1`, so root paths resolve as they do on the domain.
- Check desktop and mobile layouts, keyboard navigation, links, privacy anchors, the old-address forwards and the publisher file before merging.
- Keep the effective date and `sitemap.xml` current when changing policy wording. Update the stylesheet version in all pages when changing CSS.
- Merge the verified package into this repository's `main` and push. GitHub Pages publishes the root directory. Keep the package branch for the work history.
- Keep real download links out until their public store destinations have been verified.

## Content and privacy facts

The 6 October 2026 update (effective date 6 October 2026) covers version 1.0.4: Unity Engine Diagnostics, which builds 1.0.0 to 1.0.3 sent to Unity regardless of the in-game choices and which 1.0.4 turns off; the one-time birth-year question, of which only the age band is stored; analytics and crash choices off below 16; general-audience ad content for everyone; the Android backup limited to the save folder; and the Instagram link shown to players aged 13 and over. Implementation reference: the game repository's `docs/PRIVACY_ACCURACY.md`, `docs/AGE_AND_AD_RATING.md`, `docs/PRODUCTION_RELEASE_104.md` and `docs/INSTAGRAM_LINK.md`.

The 20 September 2026 update describes version 1.0.3's separate first-launch
analytics/crash choices, preserved choices from earlier releases, added gameplay
metrics, the Crashlytics restart/local-report limitation, and optional Google
Play updates. The support FAQ explains that users of 1.0.2 and earlier first
update through Play. Advertising privacy remains independent. Implementation
reference: the game repository's `docs/PRIVACY_METRICS_UPDATES.md` and
`docs/PRIVACY_POLICY_RELEASE_COPY.md`.

The 18 September 2026 copy was checked against the Unity project's `docs/DATA_INVENTORY.md`, `GameSettings`, `FirebaseAnalyticsService`, `AdMobAdService`, `AdConsent`, `SaveService` and English Settings labels. The first release has no IAP, no player accounts and no game-managed cloud save. Optional Firebase sharing is off by default. Advertising processing is separate and can begin while preloading, before a player watches an optional rewarded video.

Do not promise automatic recovery of progress, complete anonymity, no data processing before an ad is watched, or deletion of all provider data merely by uninstalling. The Analytics property's actual retention setting still needs verification in the service console; the policy deliberately does not claim the unconfirmed two-month target is configured. AdMob consent delivery and Play Data safety declarations require their own checks and are not certified by this website update.

Provider and policy references reviewed for the refresh:

- [Google Play User Data](https://support.google.com/googleplay/android-developer/answer/10144311?hl=en)
- [AdMob data disclosure](https://developers.google.com/admob/unity/privacy/play-data-disclosure)
- [AdMob consent integration](https://developers.google.com/admob/unity/privacy)
- [Firebase privacy and security](https://firebase.google.com/support/privacy)
- [Crashlytics opt-in reporting for Unity](https://firebase.google.com/docs/crashlytics/unity/customize-crash-reports#enable-opt-in-reporting)
- [Google Play update data safety](https://developer.android.com/guide/playcore/in-app-updates#data-safety)
- [European Commission privacy rights](https://commission.europa.eu/law/law-topic/data-protection/information-individuals_en)
- [California privacy rights](https://oag.ca.gov/privacy/ccpa)
- [GitHub Pages data collection](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages#data-collection)

## Assets and licences

- `talvero-emblem.png` and `talvero-mark.png` are the studio emblem and wordmark from the game's Talvero Games logo (`tools/art/make_studio_mark.py` in the game repository).
- `studio-hero.webp` (and its 1200 px copy) is generated studio artwork; `goalbreaker-art.webp` and `goalbreaker-feature.webp/.jpg` come from the game's store feature art; `studio-social.jpg` is the 1200×630 share image.
- The logo, icon and social cover are the game's existing official art. `social-cover.png` is the English `art/store/feature_1024x500_en.png`.
- `home.webp` is the English `tools/out/release-ui/en-home.png` capture.
- `gameplay.webp` is `tools/out/level_review/2026-09-14/new_50_final/A02_opening.png`.
- `celebration.webp` is `tools/out/level_review/2026-09-14/new_50_baseline/A20_trace_end.png`.
- WebP captures are resized/compressed exports of real game captures, with no invented gameplay. Original assets remain intact in the game repository. The older `shot-title.jpg` is retained for existing links/history but is no longer displayed.
- Barlow Condensed (800) and Nunito Sans (variable weight) are served locally as Latin WOFF2 subsets from Google Fonts. Their SIL Open Font License files are included under `assets/fonts/`.

## Verification — 20 September 2026 privacy update

- All five HTML documents pass the existing recommended HTML validation.
- All three pages at 320, 390, 768, 1024 and 1440 CSS pixels: no horizontal
  overflow or missing images. Six axe WCAG A/AA scans report zero violations.
- Eight existing navigation/keyboard/no-JavaScript checks pass. The new update
  anchor and expanded privacy/update FAQs were additionally exercised; their
  text also fits at 320 px. Mobile policy/FAQ screenshots were reviewed.
- All 82 local HTML resource/link references and fragments resolve; the browser
  recorded no page errors, failed resources or external asset requests.
- Wording was checked against the implemented 1.0.3 flow and Google's current
  Crashlytics/Play update documentation. No CSS, ad publisher record or tracking
  change. Evidence lives in the game repository under
  `tools/out/closed-test-aab-103/2026-09-20_215814/site/`.

## Verification — 18 September 2026

- All five HTML documents pass `html-validate` recommended checks.
- Home, support and privacy checked at 320, 390, 768, 1024 and 1440 CSS pixels: no horizontal overflow, clipped text or missing images after scrolling.
- Six axe WCAG A/AA scans (390 and 1440 px across the three pages): zero violations reported. Automated scans do not replace a complete accessibility audit.
- Eight interaction checks pass: FAQ keyboard open/close, policy contents, skip link focus/navigation, legacy redirect, and FAQ/redirect with JavaScript disabled.
- 101 HTML resource/link references plus CSS font resources checked; no missing local targets or fragments. No page errors, failed asset requests or external asset requests during the browser run.
- Desktop and mobile screenshots reviewed. Browser: isolated headless Chrome 153.0.8010.50; no personal browser profile. Native Safari and physical-phone checks were not part of this run.
- Both live publisher records returned HTTP 200 with `pub-4171096744461223` before deployment; their contents are unchanged.
