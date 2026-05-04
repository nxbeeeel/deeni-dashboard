# deen.in — operations status

_Last refresh: 2026-05-04T18:19:46.008Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **100.00%** |
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 7 events · 5 users · last 3d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 6 events · 4 users · last 3d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 18d ago
- REACT-NATIVE-2 — ApplicationNotResponding: ANR · 1 events · 1 users · last 30d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 68
- `Application Became Active` — 42
- `Application Opened` — 24
- `Application Installed` — 1

## GitHub — recent commits to main

- `c8f9a0a` — chore(dashboard): refresh state 2026-05-04T16:52:30Z · 1h ago
- `036fa3e` — chore(dashboard): refresh state 2026-05-04T14:40:05Z · 4h ago
- `5ac1c11` — chore(dashboard): refresh state 2026-05-04T12:11:46Z · 6h ago
- `c8873b0` — chore(dashboard): refresh state 2026-05-04T10:19:16Z · 8h ago
- `d22ac32` — chore(dashboard): refresh state 2026-05-04T07:37:32Z · 11h ago
- `9bc5e32` — chore(dashboard): refresh state 2026-05-04T04:29:20Z · 14h ago
- `762d58f` — chore(dashboard): refresh state 2026-05-04T00:12:53Z · 18h ago
- `9688391` — chore(dashboard): refresh state 2026-05-03T23:12:51Z · 19h ago
- `af0ba8a` — chore(dashboard): refresh state 2026-05-03T22:08:47Z · 20h ago
- `afd8ff4` — chore(dashboard): refresh state 2026-05-03T21:12:17Z · 21h ago

## CDN probes

- OK  `jsdelivr` — 200 · 215ms
- OK  `rawGithub` — 200 · 281ms
- OK  `everyayah` — 200 · 593ms
- OK  `quranicaudio` — 200 · 286ms
- OK  `qurancdn` — 200 · 550ms

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
