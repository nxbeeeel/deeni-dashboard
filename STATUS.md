# deen.in — operations status

_Last refresh: 2026-04-30T22:58:10.662Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **100.00%** |
| DAU | **10** |
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 6 events · 5 users · last 5d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 2 events · 2 users · last 7d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 15d ago
- REACT-NATIVE-2 — ApplicationNotResponding: ANR · 1 events · 1 users · last 26d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 67
- `Application Became Active` — 41
- `Application Opened` — 27
- `Application Installed` — 4

## GitHub — recent commits to main

- `e59dc66` — chore(dashboard): refresh state 2026-04-30T21:34:39Z · 1h ago
- `26cc838` — chore(dashboard): refresh state 2026-04-30T20:13:15Z · 3h ago
- `ab96573` — chore(dashboard): refresh state 2026-04-30T18:54:25Z · 4h ago
- `11cb464` — chore(dashboard): refresh state 2026-04-30T17:03:55Z · 6h ago
- `9d71c4a` — chore(dashboard): refresh state 2026-04-30T15:29:27Z · 7h ago
- `2ec51c4` — chore(dashboard): refresh state 2026-04-30T13:07:50Z · 10h ago
- `9922fcc` — chore(dashboard): refresh state 2026-04-30T11:16:07Z · 12h ago
- `7fbe4ef` — chore(dashboard): refresh state 2026-04-30T09:20:37Z · 14h ago
- `7ca7040` — chore(dashboard): refresh state 2026-04-30T06:36:58Z · 16h ago
- `8e6c6fe` — chore(dashboard): refresh state 2026-04-30T03:58:50Z · 19h ago

## CDN probes

- OK  `jsdelivr` — 200 · 110ms
- OK  `rawGithub` — 200 · 218ms
- OK  `everyayah` — 200 · 513ms
- OK  `quranicaudio` — 200 · 329ms
- OK  `qurancdn` — 200 · 290ms

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
