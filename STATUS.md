# deen.in — operations status

_Last refresh: 2026-05-05T08:34:46.026Z (just now)_
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 8 events · 6 users · last 1m ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 6 events · 4 users · last 3d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 19d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 55
- `Application Became Active` — 39
- `Application Opened` — 25
- `Application Installed` — 4

## GitHub — recent commits to main

- `24d3bfe` — chore(dashboard): refresh state 2026-05-05T06:26:36Z · 2h ago
- `4fabcbb` — chore(dashboard): refresh state 2026-05-05T03:58:07Z · 5h ago
- `5715d26` — chore(dashboard): refresh state 2026-05-05T00:04:04Z · 9h ago
- `5307c4e` — chore(dashboard): refresh state 2026-05-04T23:00:33Z · 10h ago
- `66a6f6f` — chore(dashboard): refresh state 2026-05-04T21:40:08Z · 11h ago
- `b490203` — chore(dashboard): refresh state 2026-05-04T20:04:14Z · 13h ago
- `7e24b58` — chore(dashboard): refresh state 2026-05-04T18:19:46Z · 14h ago
- `c8f9a0a` — chore(dashboard): refresh state 2026-05-04T16:52:30Z · 16h ago
- `036fa3e` — chore(dashboard): refresh state 2026-05-04T14:40:05Z · 18h ago
- `5ac1c11` — chore(dashboard): refresh state 2026-05-04T12:11:46Z · 20h ago

## CDN probes

- OK  `jsdelivr` — 200 · 1123ms
- OK  `rawGithub` — 200 · 232ms
- OK  `everyayah` — 200 · 483ms
- OK  `quranicaudio` — 200 · 352ms
- OK  `qurancdn` — 200 · 352ms

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
