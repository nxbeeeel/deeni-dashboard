# deen.in — operations status

_Last refresh: 2026-05-10T06:38:14.676Z (just now)_
_App version: 1.6.1 (build 52)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **100.00%** |
| DAU | **16** |
| Open bugs (`triage`) | **0** |
| In progress | **0** |
| Fixed (14d) | **0** |
| Last production deploy | **—** (unknown) |
| Last CI on main | **in_progress** |
| Active alerts | **0** |

## Open bugs (`triage`)

_None._

## In progress

_None._

## Fixed (last 14 days)

_None._

## Sentry — top 10 issues (24h)

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 8 events · 6 users · last 5d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 6 events · 4 users · last 8d ago
- REACT-NATIVE-6 — App Hanging: App hanging for at least 2000 ms. · 1 events · 1 users · last 2d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 24d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 51
- `Application Opened` — 27
- `Application Became Active` — 26
- `quran_played` — 24
- `Application Installed` — 6
- `feature_opened` — 5
- `surah_opened` — 3
- `mushaf_opened` — 1
- `prayer_marked_done` — 1
- `Application Updated` — 1

## GitHub — recent commits to main

- `7637092` — chore(dashboard): refresh state 2026-05-10T03:48:52Z · 3h ago
- `f58b410` — chore(dashboard): refresh state 2026-05-10T02:31:20Z · 4h ago
- `233e20d` — docs(field-notes): log 3 more user-reported issues for v1.6.2 · 4h ago
- `cd09bb4` — docs: add comprehensive Mushaf design spec for v1.7.0 sprint · 4h ago
- `2a1e9e1` — chore: bump version to 1.6.1 (52) · 4h ago
- `6300674` — fix(mushaf): swipe race, audio page-change reset, bismillah rendering for surah-start · 4h ago
- `22e8708` — chore(dashboard): refresh state 2026-05-10T02:18:26Z · 4h ago
- `ee15f67` — docs(field-notes): log Mushaf hot-fix issues for v1.6.1 · 4h ago
- `2e85d30` — fix(ci): track v1.4.0+ feature source files (fasting, hijri, zakat, prayer-history, duas guide, offline audio) · 5h ago
- `d8c3dcb` — fix(ci): track scripts/fix-cmake-stl.cjs (referenced by postinstall) · 5h ago

## CDN probes

- OK  `jsdelivr` — 200 · 188ms
- OK  `rawGithub` — 200 · 177ms
- OK  `everyayah` — 200 · 445ms
- OK  `quranicaudio` — 200 · 343ms
- OK  `qurancdn` — 200 · 503ms

## EAS update channels

- `production` — ? · — · unknown
- `internal` — ? · — · unknown
- `preview` — ? · — · unknown
- `development` — ? · — · unknown

## WORKLOG — last entries

- 2026-05-10 — Notification reliability overhaul (Batch 1 + 2) (`350c64c`)
  Foundation pass: USE_EXACT_ALARM permission (Android 14+ default-deny fix), stable per-prayer-per-day identifiers (`adhan_${prayer}_${YYYY-MM-DD}`), idempotent diff-based scheduling instead of cancel-all-then-recreate, default `nudgeEnabled: false` (most-reported "duplicate adhan" cause), removed iOS foreground double-playback, singleton listener guard, unified Test button. Hardening pass: self-heal listener on AppState 'active' that re-runs scheduling when scheduled count drops below threshold (catches OEM kills on Xiaomi/Samsung/Realme), versioned per-prayer channels (`adhan-fajr-v2`, etc.) with auto-bump on sound change, permission-revoked detection with `notificationsBlocked` / `timeSensitiveBlocked` flags, new Notification Health screen at /settings/notification-health (count, next 5, permissions, re-schedule action, OS settings deep link).
- 2026-05-10 — PostHog product-feature event capture (`7071a75`)
  Previously only lifecycle events flowed (Application Opened/Backgrounded). Now captures: `quran_played` (surah, ayah, reciter, mode), `prayer_marked_done` (prayer, on_time — best-effort via cachedPrayerTimes within ±6h), `bookmark_added` (verse + page variants), `translation_downloaded` (edition, verse_count), `surah_opened`, `mushaf_opened`, `feature_opened` (home tools grid), `adhan_notification_opened` (via singleton response listener filtered on data.type='adhan'). All gated on null-safe wrapper; non-throwing.
- 2026-05-10 — Mushaf layout migration to verified Madani source (`a113949`)
  User-reported "many ayah ending mistakes" was a layout bug, not a text bug. Old generator used quran.com word-level `line_number` calibrated for QPC glyph fonts — when rendered as plain Uthmani text, end-of-verse markers (numerals) appeared on the line AFTER where the verse actually finishes. Sample of 30 random pages: 15/30 had at least one misplaced marker, 60 total mismatched lines. Wrote new generator using King Fahd Madani layout reference (zonetecde/mushaf-layout) for line/page boundaries, kept quran.com `text_uthmani` for verse text (text itself was correct). Regenerated `assets/data/mushaf-pages.json`: 0/30 mismatches after fix. Schema unchanged — fully backward-compatible. Added `npm run generate:mushaf:tanzil` script.
- 2026-05-10 — Sentry production-error guards (`7684acf`)
  Two top Sentry issues (8 events / 6 users + 6 events / 4 users in 24h) traced to missing try/catch: 1. `ExpoLocation.removeWatchAsync rejected` in qibla screen cleanup — wrapped each `.remove()` call individually so failure on one doesn't prevent the other; logs via `console.warn`, doesn't throw from cleanup. 2. `NativeDatabase.prepareSync rejected` in offline translation manager — wrapped all 5 sync DB calls (runSync, getFirstSync, getAllSync) with sensible fallbacks: `false` for isDownloaded checks, `[]` for getDownloadedEditions, `0` for verse count, structured throws for downloadTranslation so callers can surface to user. 3. Module.swift `updateActivity` and `endActivity` converted to `AsyncFunction` (matching `startActivity` from earlier commit) — eliminates fire-and-forget pattern where JS got "ended" before ActivityKit work completed.
- 2026-05-10 — Word-by-word Quran audio synchronisation (`fca4bd0`)
  Previously highlighting was tap-driven only — no connection to audio playback. Now: when audio is playing the displayed ayah AND the reciter is in the QDC-supported set (Mishary 7, Sudais 2, Abdul Basit 1, Husary 5), fetch per-word timing data from `api.qurancdn.com/api/qdc/audio/reciters/{id}/audio_files` (audio_segments tuples), increase `expo-audio` `updateInterval` from default 500ms to 100ms, and drive `activeWordIndex` from current playback position. Bounded-LRU cache (50 entries), Hermes-safe AbortController + setTimeout (replaced `AbortSignal.timeout` which crashes on Hermes), full-surah mode gated to prevent stale per-ayah timings during full-surah playback.
- 2026-05-10 — iOS widget bridge + Live Activity race fix + design parity (`2a3a5bb`)
  Bridge: `checkWidgetBridgeAvailable()` exposed for early-return guards, `__DEV__` console.warn when native module is null (was silent no-op). Live Activity `startActivity` converted from `Function` + `Task { }` (race: end-old + request-new fired in parallel, ActivityKit's 1-activity-per-app limit silently rejected the new request) to `AsyncFunction` with sequential `await` of all `activity.end()` before `Activity.request()`. Design pass: 1px white@0.12 ContainerRelativeShape stroke on NextPrayer + PrayerTimes widgets, 3-stop deeper gradient (0/0.6/1.0), gold (#E2C98B) accent for secondary text (countdown timer, location), Live Activity lock screen wrapped in ZStack with gradient bg + RoundedRectangle 16pt border.
- 2026-05-10 — Quran screen performance pass (`792aeec`)
  FlatList perf: extracted `SurahListItem` as top-level `memo()` component, `renderItem` and handlers wrapped in `useCallback`, `ListHeaderComponent` JSX moved into `useMemo`, fixed `directAyahMatch` raw-const dep that busted `filteredSurahs` memo every render. `[surah].tsx`: `loadVerses` useCallback with correct deps, `renderItem` useCallback, `ListFooterComponent` useMemo, all bookmark handlers memoized. `mushaf.tsx`: `pageTitle`, `currentVerseKey`, `gridSlots`, `panResponder` useMemo. Then second pass: extracted 5 inline style array literals from inside `SurahListItem` body to defeat shallow-comparison bypass; removed unused `width` dep from `panResponder` deps array. Final pass: `[surah].tsx` switched from full-store destructure to 5 sliced `useAudioStore(s => ...)` selectors so the screen doesn't re-render 10×/sec under Task 9's faster tick rate.
- 2026-05-10 — Reciter URL audit (full-surah mode) (`a09f6ea`)
  Live-tested all reciter URLs against quranicaudio.com/qdc CDN. 5 wrong slugs corrected (Husary murattal, Husary muallim, Minshawy murattal, Abu Bakr Shatri, Yasser Ad-Dussary). 15 reciters had no QDC entry — `fullSurahSlug` removed from those entries; they fall back cleanly to per-ayah everyayah.com (all per-ayah URLs tested clean). All 25 reciters preserved in the array.
- 2026-05-10 — iPhone haptic feedback throughout app (`09a8044`)
  expo-haptics added to: play/pause buttons (Medium impact), surah navigation (Light), bookmark add (Success notification), prayer mark-done (Success), prayer un-mark (Light), Mushaf page nav (Light), Mushaf bookmark add (Success). No haptic on tap-only interactions to avoid noise.
- 2026-05-10 — iOS time-sensitive prayer notifications (`6554627`)
  Added `interruptionLevel: 'timeSensitive'` to both adhan + nudge notification content (iOS 15+ — bypasses Focus mode for users who grant Time Sensitive permission). Explicit iOS permission flags in `requestPermissionsAsync`: `{ ios: { allowAlert: true, allowSound: true, allowBadge: true } }`. Schedule horizon extended from "today only" to 7 days × 5 prayers = 35 notifications max (well under iOS 64-limit). Then removed invalid option `allowDisplayInNotificationCenter` (not part of expo-notifications iOS permission shape).
