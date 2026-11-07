# Orbit Hop '89 — Privacy & Support (Phase 4.1)

Two English, buildless HTML pages for the existing BabiLabs GitHub Pages site:

- `https://babilabs.github.io/orbit-hop/privacy/`
- `https://babilabs.github.io/orbit-hop/support/`

These are the selected deployment targets. See the release report below for
verification status; source files alone are not proof of publication.

## Hosting and publishing

On 7 November 2026, GitHub's Pages API confirmed this public repository serves
`main` from `/`, with HTTPS enforced and `cname: null`. The existing root returned
HTTP 200. Both `https://babilabs.com/orbit-hop/privacy` and
`https://babilabs.com/orbit-hop/support` redirected to `www.babilabs.com` on
Squarespace and returned HTTP 404. Do not add a CNAME or use those product URLs
without separately configuring and verifying that domain.

Commit and push these files to `main`; the existing GitHub Pages branch build
publishes them without dependencies or a custom build workflow. Confirm the
Pages build succeeds and both new HTTPS routes return 200 with the expected
content before changing store listings or claiming reachability. Directory
routes also support explicit `index.html` paths; check the no-trailing-slash
routes used by the app redirect successfully.

**App integration still required:** in the separate `orbithop` repository, change
`lib/branding/release_info.dart` to the two verified GitHub Pages URLs, then
rebuild the app. This website change does not repair URLs baked into existing
installed builds. No files in that separate repository were edited here.

## Evidence reviewed before writing

App source: `/mnt/projects/orbithop`, commit
`9b30adf4991765883da7a985956bc631c804b4ed` (clean at review).

- `docs/PRIVACY_SDK_AUDIT.md` (6 November 2026): published SDK source samples,
  native plugin behavior, platform distinctions and binary-review limits.
- `pubspec.yaml`: Flutter; Flame `^1.38.2`; shared_preferences `^2.5.3`;
  audioplayers `^6.5.1`. No lockfile, resolved native dependency inventory or
  signed release binary was available. These are constraints, not verified
  installed release versions.
- `lib/persistence/local_store.dart`, `local_scores.dart`,
  `lib/journey/journey_repository.dart`, `journey_run.dart`: actual stored fields,
  local top ten and checkpoint behavior. `clearScores()` clears leaderboard
  entries only, retaining personal bests and Journey data.
- `lib/audio/retro_audio.dart`: bundled `AssetSource` playback only. Native
  plugin source samples were reviewed by the existing audit; no claim that they
  match an uploaded TestFlight build is made.
- Android main/release manifests, app/root Gradle and settings: Flutter plugin,
  no ad/analytics integration, backup disabled, release internet/network-state/
  advertising-ID removals. Final merged permissions still require binary review.
- iOS `Info.plist`, `PrivacyInfo.xcprivacy`, native browser handlers: preference
  reason CA92.1, no app-declared tracking/collection, explicit system-browser
  HTTPS opening. SDK manifests in the final archive still require review.
- `docs/ENDLESS_ARCADE.md`, current level catalog and UI: current Endless rules,
  five Journey worlds, settings labels and checkpoint options. Historical
  Phase 2A notes are superseded by current source.
- Repository `index.html`, `legal/index.html`, `privacy/index.html` and
  `sporti-plan/README.md`: published BabiLabs contact `babilabs@duck.com`,
  operator Ali Babi, postal street and DuckDuckGo forwarding to GMX. This is
  documentary confirmation of the address, not a mailbox delivery test.

Provider references linked from the policy: Apple/Google privacy notices,
[GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement),
[DuckDuckGo Email Protection](https://duckduckgo.com/email/privacy-terms), and
[GMX privacy](https://agb-server.gmx.net/datenschutz/).

## Remaining privacy/release questions

1. Review and commit the resolved `pubspec.lock`, compare Android/iOS SDK
   inventories, merged Android manifest/permission export and iOS archive privacy
   report. Confirm native offline behavior and linked SDK processing.
2. Verify iOS/device backup and restore behavior; Android's source disables
   backup. Do not promise that every backup or device migration excludes saves.
3. Confirm a support-email retention/deletion schedule, provider arrangements
   and applicable international-transfer safeguards. The policy flags these
   omissions rather than inventing terms or assurances.
4. Confirm the operator's postal code to complete the documented street address.
   Reassess applicable disclosure requirements for the actual distribution
   countries before final store submissions. No legal clearance is claimed.
5. Do not submit blanket “Data Not Collected” store answers based on this website
   or source audit alone. Update the policy if release verification changes facts.

## Implementation and maintenance

No JavaScript, tracking, cookies, remote assets, forms, analytics or framework.
The only page-load resources are local CSS, logo, favicon and font. External
policy links and mail links are user initiated. Hosting still processes connection
data; emailing support has separate processing described in the policy.

Shared stylesheet: `assets/styles.css`. Pixel typography is reserved for headings
and labels; body text uses system fonts. Responsive layouts collapse at 900/640px,
with visible keyboard focus, skip link, semantic navigation and native FAQ details.
Logo copied from the game under MIT (`assets/ARTWORK-LICENSE.txt`); OrbitPixel is
Press Start 2P under SIL OFL (`assets/OFL.txt`). Favicon is a local SVG.

Review content when SDKs, saves, providers, contact details or platform behavior
change. Keep the app URLs and store listings aligned with verified hosting.
