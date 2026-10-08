# Talvero Games website

The website of Talvero Games at https://talverogames.com: the studio home page and the Goalbreaker pages in English, with Turkish versions of the home and Goalbreaker pages under `/tr/`. Static HTML and CSS on GitHub Pages with a custom domain; no build step, website analytics or third-party font requests. JavaScript appears only in the one-line forwards of the old addresses and in the small language-preference script of the four bilingual pages; the home and Goalbreaker pages carry JSON-LD structured data.

## Addresses

| Use | URL |
| --- | --- |
| Studio home; Play "Website" field | https://talverogames.com/ |
| Goalbreaker | https://talverogames.com/goalbreaker/ |
| Studio home in Turkish | https://talverogames.com/tr/ |
| Goalbreaker in Turkish | https://talverogames.com/tr/goalbreaker/ |
| Privacy policy | https://talverogames.com/goalbreaker/privacy/ |
| Support | https://talverogames.com/goalbreaker/support/ |
| AdMob publisher record | https://talverogames.com/app-ads.txt |

`privacy.html`, `gizlilik.html` and `support.html` at the root forward to the new pages and keep the `#fragment` (meta refresh plus `location.replace`, both relative so they also work on the github.io project address). Released game versions open `https://dogukanscz.github.io/goalbreaker-site/privacy.html` and `.../gizlilik.html`. GitHub forwards that project address to `https://talverogames.com/<same path>` as long as the custom domain is set, and the root files then forward again. Keep all three files and the section ids of the policy.

`404.html` serves every missing path of the domain, so its links and assets use root paths (`/...`); it has no `<base>` element, which would send its skip link to the home page.

## Languages

- `/` and `/goalbreaker/` are English; `/tr/` and `/tr/goalbreaker/` are their Turkish versions. The four pages list each other with `hreflang="en"`, `hreflang="tr"` and `hreflang="x-default"` (English), and carry an EN/TR link in the header. Update both languages together.
- The privacy policy and support pages exist only in English and carry no `hreflang`. The Turkish pages mark every link to them with `hreflang="en"`, and the in-page links (game card, FAQ, resource cards) also say "(İngilizce)"; header and footer links do not. `gizlilik.html` still forwards to the English policy.
- A small inline script in the `<head>` of the four bilingual pages reads `data-alt-lang` and `data-alt-href` on `<html>`. On an English page it opens the Turkish version when the stored choice is `tr`, or when nothing is stored, the browser's first language is Turkish (`tr` or `tr-…`) and the visitor did not come from a Turkish page (with storage blocked: from no page of this site); on a Turkish page it opens the English version only when the stored choice is `en`. Clicking the EN/TR link stores `talvero-lang` = `en` or `tr` in `localStorage`; nothing else is stored, nothing is sent anywhere, and there is no IP or country redirect. Without JavaScript the pages simply stay where they are; with storage blocked the EN/TR link still works, but the choice is not remembered. The privacy, support and 404 pages have no script.
- Turkish copy follows the game's Play listing wording (`STORE_LISTING.md` in the game repository): "Goalbreaker: Futbol Bulmaca", "Vuruşu çiz, duvarı yık, gol at.", "bölüm" for chapters, "seviye" for levels, "günlük duvar" for daily walls.

## Domain

- `CNAME` holds `talverogames.com`; Pages publishes `main` from the root (branch build). The domain is registered at Cloudflare Registrar (renews automatically; keep the payment method valid).
- Cloudflare DNS, every record **DNS only** (grey cloud) so GitHub can issue the certificate:
  - four `A` records on `@`: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`;
  - four `AAAA` records on `@`: `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`;
  - `CNAME` `www` to `dogukanscz.github.io` (GitHub forwards `www` to the bare domain);
  - do not delete: the `google-site-verification` TXT on `@` (Search Console domain property), the `_github-pages-challenge-dogukanscz` TXT, `v=spf1 -all` on `@` and `v=DMARC1; p=reject;` on `_dmarc` (the domain sends no mail). Add any new verification record (Bing, Yandex) here, as DNS only.
- Never proxy a record (orange cloud) and never turn on Cloudflare Web Analytics or other proxy features: the privacy policy's "Privacy on this website" section names GitHub Pages as the host and promises no analytics.
- "Enforce HTTPS" is turned on once GitHub has issued the certificate.
- `app-ads.txt` must stay at the domain root. The older copy at `https://dogukanscz.github.io/app-ads.txt` comes from the separate `dogukanscz.github.io` repository and stays while any listing still points at github.io.

## Editing and publishing

- Start a package branch from current `origin/main` (this **website repository** publishes from `main`; the separate Unity repository's frozen `main` is unrelated).
- Edit the HTML directly. Preview locally from the repository root with `python3 -m http.server 8765 --bind 127.0.0.1`, so root paths resolve as they do on the domain.
- Check desktop and mobile layouts, keyboard navigation, links, privacy anchors, the old-address forwards and the publisher file before merging.
- Keep the effective date and `sitemap.xml` current when changing policy wording, and update a page's `lastmod` when its content changes.
- When changing CSS, update the stylesheet version (`style.css?v=YYYYMMDD`) in every page you touch. The three root forwards keep their old version; they show only the redirect text. CSS changes must not alter how the privacy and support pages look unless that is the intended change: put new rules on new classes, and check those two pages before and after.
- Merge the verified package into this repository's `main` and push. GitHub Pages publishes the root directory. Keep the package branch for the work history.
- Keep real download links out until their public store destinations have been verified. Launch-day order: check that the Play listing loads; then add the Google Play badge and link, the Play URL in the game's JSON-LD `sameAs` (add no `offers` block: Google's software-app markup requires `offers.price`, a price of 0 would call the game free, and without ratings of the site's own the rich result stays out of reach), update the FAQ answer "When can I play it?" and the "Coming soon" lines in both languages; only then post the "Now on Google Play" stories.

## Content and privacy facts

The 8 October 2026 update (effective date 8 October 2026) was checked against version 1.0.5, which changes no data flow of 1.0.4. It adds a Türkiye (KVKK, Law No. 6698) paragraph to the regional rights: explicit consent for the optional analytics and crash reports, the Article 11 rights, requests by email answered within 30 days, and complaints to the Personal Data Protection Board. The children's section now says that under 16 the game asks Google's ad service for its child protections, and that neither the birth year nor the age range is sent. The advertising section says that the game requests no ads and shows no advertising message before the age question is answered (`AdBoot`). The website section describes the `talvero-lang` language entry in local storage and the browser-language forward of the bilingual pages. A lawyer has not reviewed the KVKK paragraph; open questions are the law's formal application channels, a Turkish version of the policy and the transfer-abroad rules (Article 9).

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

- `talvero-emblem.png` and `talvero-mark.png` are the studio emblem and wordmark from the game's Talvero Games logo (`tools/art/make_studio_mark.py` in the game repository). `talvero-emblem-144.webp` and `talvero-mark.webp` are WebP copies (cwebp q85) used by the home, Goalbreaker, Turkish and 404 pages; the policy pages and forwards keep the PNGs.
- `talvero-icon-192.png`, `talvero-touch-icon-180.png` and the root `favicon.ico` (48 px) are a centred 700 px square crop of the studio's Instagram profile picture (`instagram/talverogames_profile.png`); Google Search needs a square favicon on the home page. `talvero-logo-512.png` is the 512 px Instagram profile lockup (`instagram/talverogames_profile_lockup.png`), used as the Organization logo in structured data because it reads on white.
- `ig-goalbreakergame.webp` is a 224 px copy of the game's Instagram profile picture (`instagram/goalbreakergame_profile.png`), shown in the Goalbreaker launch band. Do not hotlink Instagram's images or embed its widgets.
- `studio-hero-phone.webp` is a 920×708 crop of `studio-hero.webp` (the stadium and ball) shown above the hero copy on screens up to 800 px. `logo-goalbreaker.webp` is a WebP copy of the game logo at its native 640×155.
- `studio-hero.webp` (and its 1200 px copy) is generated studio artwork; `goalbreaker-art.webp` and `goalbreaker-feature.webp/.jpg` come from the game's store feature art; `studio-social.jpg` is the 1200×630 share image.
- The logo, icon and social cover are the game's existing official art. `social-cover.png` is the English `art/store/feature_1024x500_en.png`.
- `home.webp` is the English `tools/out/release-ui/en-home.png` capture.
- `gameplay.webp` is `tools/out/level_review/2026-09-14/new_50_final/A02_opening.png`.
- `celebration.webp` is `tools/out/level_review/2026-09-14/new_50_baseline/A20_trace_end.png`.
- WebP captures are resized/compressed exports of real game captures, with no invented gameplay. Original assets remain intact in the game repository. The older `shot-title.jpg` is retained for existing links/history but is no longer displayed.
- Barlow Condensed (800) and Nunito Sans (variable weight) are served locally as Latin and Latin Extended WOFF2 subsets from Google Fonts (the same font versions; the Latin Extended files add ğ, ş and İ and load only on pages that use them). Their SIL Open Font License files are included under `assets/fonts/`.
- The Instagram glyph is a single-colour inline SVG of at least 29 px, always next to a call to action or an @handle, with half the glyph's size (15 px) of clear space between them; in the header the "Follow" / "Takip et" label sits under the glyph up to 1050 px. Use no Instagram gradients.
- `goalbreaker-feature-tr.jpg` is the Turkish store feature graphic (`art/store/feature_1024x500_tr.png` in the game repository), the share image of `/tr/goalbreaker/`.

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
