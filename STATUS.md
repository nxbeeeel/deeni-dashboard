# deen.in — operations status

_Last refresh: 2026-05-11T01:27:07.140Z (just now)_
_App version: 1.7.6 (build 64)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **—** |
| DAU | **11** |
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

_Sentry pull failed: The operation was aborted due to timeout_

## PostHog — top events (24h)

- `Application Backgrounded` — 51
- `quran_played` — 32
- `Application Opened` — 28
- `Application Became Active` — 26
- `surah_opened` — 8
- `mushaf_opened` — 3
- `prayer_marked_done` — 2
- `feature_opened` — 2
- `Application Installed` — 2
- `Application Updated` — 1

## GitHub — recent commits to main

- `cc7eb48` — feat(quran-foundation): Connected Apps integration scaffolding (Phase 0) · 18m ago
- `be91bd7` — feat(mushaf): design v2 Batches B-E + v1.7.6 release (single hairline, SVG lobed-oval cartouche, restrained traditional) · 26m ago
- `9167013` — feat(mushaf): design v2 Batch A — color system (palette, 4-mode toggle, theme reads) · 45m ago
- `b8effc0` — docs(plans): mushaf design v2 implementation plan (v1.7.6) — 5 batches, awaiting approval · 58m ago
- `70ae6da` — fix(build): re-disable Sentry source-map auto-upload — was breaking Gradle on EAS · 1h ago
- `b26bffa` — ci(release): revert to GitHub-secret-based credential restore · 1h ago
- `74c73f4` — ci(release): funnel GOOGLE_PLAY_SERVICE_ACCOUNT_KEY_BASE64 secret via job-level env · 1h ago
- `0a9e941` — fix(mushaf): wire QPC font registration + tighten Amiri layout (v1.7.5) · 1h ago
- `a49dd06` — chore(dashboard): refresh state 2026-05-10T23:53:50Z · 2h ago
- `6f33bd8` — docs(plans): mushaf QPC font fix + layout v2 plan (research-grounded, awaiting approval) · 2h ago

## CDN probes

- OK  `jsdelivr` — 200 · 118ms
- OK  `rawGithub` — 200 · 142ms
- OK  `everyayah` — 200 · 455ms
- OK  `quranicaudio` — 200 · 233ms
- OK  `qurancdn` — 200 · 344ms

## EAS update channels

- `production` — ? · — · unknown
- `internal` — ? · — · unknown
- `preview` — ? · — · unknown
- `development` — ? · — · unknown

## WORKLOG — last entries

- 2026-05-10 — Strategy + engineering uplift (PARTS 1–6)
  Commits: 587f793 (gitignore + LF enforcement), 49a1374 (release.yml graceful skip), 89a7a9f (v1.7.x plan docs + FIELD_NOTES), 81d4076 (1.7.0 release-notes tightened + locales/screenshots/banner), 375261a (ios widget entitlements + marketing site source), 0fcc0d5 (bug-solving playbook + Claude dev ecosystem brief), 6efa3ea (/ship slash command + tsc hook + INSTALL.md), e741961 (Q3-2026 strategy memo) Six-part pre-push and engineering uplift after the v1.7.3 hotfix landed. Cleaned the working tree (committed FIELD_NOTES, plan docs, store-listing tightening, site/, ios/ widget entitlements; gitignored 28MB of design assets + HLS chunks; added `.gitattributes` for LF-only normalization across Windows/Linux to stop EAS hash drift). Fixed `.github/workflows/release.yml` — replaced step-level `if: env.X` guards (which never worked because env was step-local) with a preflight that validates every credential end-to-end (presence + valid base64 + plausible content), writes ANDROID_READY/IOS_READY to GITHUB_ENV, and gates each downstream step. First green release-workflow run in project history (graceful-skipped both platforms with clear `::warning::` log messages instead of going red). Wrote two long engineering docs — `docs/engineering/bug-solving-playbook.md` (intake card format, severity ladder, Sentry→GH auto-ingest wiring, repro harness ladder, the iron 3-failed-fixes architecture-review rule, 5-min post-mortem template) and `docs/engineering/claude-dev-ecosystem.md` (3,800 words: install/evaluate/skip across plugins, MCPs, OSS agentic tooling, marketplaces, best-practice posts, with cost-routing advice — Sonnet default / Opus arch-only / Haiku one-shots → realistic 50-70% bill cut). Wired two concrete Claude Code additions: a `/ship` slash command at `.claude/commands/ship.md` that codifies the bump → CHANGELOG → 8-locale release notes → tag → push → workflow-watch dance (saves ~30 min per release), and a `PostToolUse` hook at `.claude/hooks/typecheck-after-edit.mjs` that runs `tsc --noEmit` after TS/TSX edits and feeds relevant errors back via additionalContext (smoke-tested clean + skip paths). Plus `.claude/INSTALL.md` listing the plugin checklist for the rest. Closed with `docs/strategy/Q3-2026-thinking.md` — 290-line memo ranking the next three product moves: iOS App Store launch (1, 4-6 days, biggest multiplier), Hifz mode with SM-2 spaced repetition (2, 3 weeks, defensible differentiator), "Support deen.in" patron flow (3, 1 week, story multiplier not revenue play). Includes alternatives considered and rejected, sequencing through Q3, and honest gaps a real team would close that we won't.
- 2026-05-10 — v1.7.3 audio control hotfix (`f9c1da6`)
  Two user-reported audio bugs from device-testing of v1.7.2 patched within the session and shipped as v1.7.3. Per-ayah pause button on `app/quran/[surah].tsx` was unconditionally calling `loadAndPlay` regardless of state — tapping pause silently restarted the verse from the top instead of pausing. Replaced with a three-branch toggle: same verse + playing → `pauseAudio`; same verse + paused but loaded → `playAudio`; otherwise → `loadAndPlay`. Required adding `isPlaying`, `pauseAudio`, `playAudio` selectors to the existing `useAudioStore` slice. Word-by-word tap audio race: rapid taps were starting overlapping `createAudioPlayer` flows, and whichever finished loading last would win — sometimes that wasn't the word the user last tapped. Added a `wordPlayGenRef` generation counter (`useRef(0)`) with three guard checks (after createAudioPlayer, in `onPlaybackStatusUpdate` listener, before `play()`) so any stale call from a previous tap releases its player and bails. Bumped versionCode 57→58 / iOS buildNumber 19→20. Wrote 8 locale release notes (en-US, en-GB, ar, hi-IN, ml-IN, ms, tr-TR, ur) plus combined.txt, all verified under Play Console's 500-codepoint cap. Tagged v1.7.3 and pushed; release workflow ran green for the first time.
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

## Refresh errors

- **sentry** — The operation was aborted due to timeout
