# deen.in — operations status

_Last refresh: 2026-05-03T04:29:52.934Z (just now)_
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 7 events · 5 users · last 2d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 6 events · 4 users · last 1d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 17d ago
- REACT-NATIVE-2 — ApplicationNotResponding: ANR · 1 events · 1 users · last 28d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 60
- `Application Opened` — 35
- `Application Became Active` — 26
- `Application Installed` — 5

## GitHub — recent commits to main

- `7595bbf` — chore(dashboard): refresh state 2026-05-03T00:10:25Z · 4h ago
- `28f4946` — chore(dashboard): refresh state 2026-05-02T23:12:21Z · 5h ago
- `df6929b` — chore(dashboard): refresh state 2026-05-02T22:08:20Z · 6h ago
- `694a7f5` — chore(dashboard): refresh state 2026-05-02T21:10:50Z · 7h ago
- `cc3c91d` — chore(dashboard): refresh state 2026-05-02T20:06:07Z · 8h ago
- `bbd153f` — chore(dashboard): refresh state 2026-05-02T19:09:05Z · 9h ago
- `2d8b0ea` — chore(dashboard): refresh state 2026-05-02T17:53:23Z · 11h ago
- `ccb7563` — chore(dashboard): refresh state 2026-05-02T16:57:02Z · 12h ago
- `9626245` — chore(dashboard): refresh state 2026-05-02T15:54:06Z · 13h ago
- `c8949d1` — chore(dashboard): refresh state 2026-05-02T14:54:45Z · 14h ago

## CDN probes

- OK  `jsdelivr` — 200 · 653ms
- OK  `rawGithub` — 200 · 218ms
- OK  `everyayah` — 200 · 555ms
- OK  `quranicaudio` — 200 · 450ms
- OK  `qurancdn` — 200 · 476ms

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
