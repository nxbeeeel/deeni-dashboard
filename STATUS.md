# deen.in — operations status

_Last refresh: 2026-05-09T23:55:44.048Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **100.00%** |
| DAU | **14** |
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

- `Application Backgrounded` — 41
- `Application Opened` — 26
- `Application Became Active` — 17
- `Application Installed` — 3

## GitHub — recent commits to main

- `6e442ea` — fix(widgets): convert updateActivity/endActivity to AsyncFunction · 38m ago
- `7684acf` — fix(sentry): guard ExpoLocation cleanup + offline.ts sync DB calls · 40m ago
- `d619cf7` — perf(quran): use sliced selectors in surah reader to avoid 10Hz re-renders · 45m ago
- `100782c` — fix(quran): word-timing Hermes compatibility, cache bounds, full-surah mode · 2h ago
- `fca4bd0` — feat(quran): word-by-word audio synchronisation · 2h ago
- `1eec253` — feat(ios-widgets): visual polish pass — GlassSurface parity · 2h ago
- `2a3a5bb` — fix(widgets): resolve iOS bridge null-module visibility + Live Activity race condition · 2h ago
- `0a234f2` — fix(perf): extract inline style arrays in SurahListItem; drop unused width dep from panResponder · 2h ago
- `792aeec` — perf(quran): reduce re-renders in Quran screens with memo/useCallback/useMemo · 2h ago
- `a09f6ea` — fix(reciters): correct and remove broken fullSurahSlug values (live URL audit) · 2h ago

## CDN probes

- OK  `jsdelivr` — 200 · 103ms
- OK  `rawGithub` — 200 · 215ms
- OK  `everyayah` — 200 · 466ms
- OK  `quranicaudio` — 200 · 367ms
- OK  `qurancdn` — 200 · 367ms

## EAS update channels

- `production` — ? · — · unknown
- `internal` — ? · — · unknown
- `preview` — ? · — · unknown
- `development` — ? · — · unknown

## WORKLOG — last entries

- 2026-04-25 — Operations dashboard scaffolded
  Built the .dashboard/ refresher (Node stdlib, no deps), GitHub Actions workflow, public deeni-dashboard scaffold, password-gated Linear-style HTML, alert engine, and STATUS.md generator. Plan in DASHBOARD_PLAN.md. Awaiting first run after Phase 0 token setup.
- 2026-04-25 — iOS widgets premium redesign
  Live ticking countdown via Text(timerInterval:countsDown:), accent-rail next-prayer highlight on the Times widget, gold pull-quote treatment on Daily Dua, oversized quote-glyph backdrop on Daily Hadith. iOS 18 tinted-mode safe via widgetAccentable + widgetRenderingMode environment.
- 2026-04-25 — iOS Next Prayer widget stuck on "in 0:00" (`5302c33`)
  Root cause: src/widgets/syncWidgetData.tsx returned early on iOS so App Group group.in.deen.app was never written. Widget fell back to placeholder sample, system overlaid stale-data spinner. Fix: bridge through requireNativeModule('ReactNativeWidgetExtension')'s setString + reloadAllTimelines, wire 7-day schedule sync via syncPrayerScheduleToWidget.
- 2026-04-25 — DB + OTA hardening (`73856e0`)
  WAL journal_mode + foreign_keys=ON pragmas on every open; AppState listener that re-opens the SQLite handle on Android foreground after potential TRIM_MEMORY invalidation; runtimeVersion switched from hardcoded "1.3.4" to { policy: "fingerprint" }; Sentry tags for app.version / platform / build.number; bootstrap captureException; DB breadcrumbs in offline.ts.
- 2026-04-25 — v1.4.0 bump + expo-audio migration (`5449ae8`)
  Migrated adhanPlayer + ruqyah screen from deprecated expo-av to expo-audio. Wrapped void-returning setActiveForLockScreen / clearLockScreenControls in try/catch instead of .catch(). Added optional context/repetitions/quranRefs to RuqyahVerse. bump-version.mjs now keeps semver, versionCode, buildNumber, and package.json synced in lockstep.
