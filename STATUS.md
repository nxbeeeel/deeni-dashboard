# deen.in — operations status

_Last refresh: 2026-05-07T22:06:06.055Z (just now)_
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 8 events · 6 users · last 3d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 6 events · 4 users · last 6d ago
- REACT-NATIVE-6 — App Hanging: App hanging for at least 2000 ms. · 1 events · 1 users · last 2h ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 22d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 99
- `Application Became Active` — 75
- `Application Opened` — 33
- `Application Installed` — 3

## GitHub — recent commits to main

- `e5f548d` — chore(dashboard): refresh state 2026-05-07T20:49:34Z · 1h ago
- `7bd337c` — chore(dashboard): refresh state 2026-05-07T19:16:45Z · 3h ago
- `4db5a79` — chore(dashboard): refresh state 2026-05-07T17:18:53Z · 5h ago
- `9f05ebe` — chore(dashboard): refresh state 2026-05-07T15:15:59Z · 7h ago
- `459925f` — chore(dashboard): refresh state 2026-05-07T12:20:14Z · 10h ago
- `a3bd546` — chore(dashboard): refresh state 2026-05-07T10:30:37Z · 12h ago
- `ca71966` — chore(dashboard): refresh state 2026-05-07T07:50:39Z · 14h ago
- `3da5026` — chore(dashboard): refresh state 2026-05-07T05:00:43Z · 17h ago
- `ef4f957` — chore(dashboard): refresh state 2026-05-07T01:19:46Z · 21h ago
- `d336c5f` — chore(dashboard): refresh state 2026-05-06T23:29:24Z · 23h ago

## CDN probes

- OK  `jsdelivr` — 200 · 108ms
- OK  `rawGithub` — 200 · 162ms
- OK  `everyayah` — 200 · 498ms
- OK  `quranicaudio` — 200 · 226ms
- OK  `qurancdn` — 200 · 390ms

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
