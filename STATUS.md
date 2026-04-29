# deen.in — operations status

_Last refresh: 2026-04-29T09:14:02.390Z (just now)_
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 6 events · 5 users · last 3d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 2 events · 2 users · last 6d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 13d ago
- REACT-NATIVE-2 — ApplicationNotResponding: ANR · 1 events · 1 users · last 25d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 49
- `Application Became Active` — 24
- `Application Opened` — 23
- `Application Installed` — 2

## GitHub — recent commits to main

- `4b2350e` — chore(dashboard): refresh state 2026-04-29T06:31:20Z · 3h ago
- `50d6fc1` — chore(dashboard): refresh state 2026-04-29T03:57:09Z · 5h ago
- `87c4593` — chore(dashboard): refresh state 2026-04-28T23:59:32Z · 9h ago
- `a0ecf68` — chore(dashboard): refresh state 2026-04-28T22:33:29Z · 11h ago
- `25a6b6f` — chore(dashboard): refresh state 2026-04-28T21:14:09Z · 12h ago
- `7ee1549` — feat(dashboard): field notes — log user-reported issues via Telegram · 12h ago
- `0848f84` — chore(dashboard): refresh state 2026-04-28T21:12:33Z · 12h ago
- `008699c` — chore(dashboard): refresh state 2026-04-28T21:05:14Z · 12h ago
- `4325753` — chore(dashboard): refresh state 2026-04-28T21:00:47Z · 12h ago
- `773784e` — chore(dashboard): refresh state 2026-04-28T20:55:08Z · 12h ago

## CDN probes

- OK  `jsdelivr` — 200 · 245ms
- OK  `rawGithub` — 200 · 244ms
- OK  `everyayah` — 200 · 1370ms
- OK  `quranicaudio` — 200 · 232ms
- OK  `qurancdn` — 200 · 354ms

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
