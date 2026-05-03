# deen.in — operations status

_Last refresh: 2026-05-03T17:54:49.672Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **100.00%** |
| DAU | **17** |
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
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 6 events · 4 users · last 2d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 17d ago
- REACT-NATIVE-2 — ApplicationNotResponding: ANR · 1 events · 1 users · last 29d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 90
- `Application Became Active` — 50
- `Application Opened` — 45
- `Application Installed` — 8

## GitHub — recent commits to main

- `8ea3708` — chore(dashboard): refresh state 2026-05-03T16:58:34Z · 56m ago
- `1238860` — chore(dashboard): refresh state 2026-05-03T15:54:17Z · 2h ago
- `1b94f6e` — chore(dashboard): refresh state 2026-05-03T14:31:18Z · 3h ago
- `a146a42` — chore(dashboard): refresh state 2026-05-03T13:23:45Z · 5h ago
- `8484d70` — chore(dashboard): refresh state 2026-05-03T11:50:46Z · 6h ago
- `a3c6f26` — chore(dashboard): refresh state 2026-05-03T10:33:13Z · 7h ago
- `5159d57` — chore(dashboard): refresh state 2026-05-03T09:06:07Z · 9h ago
- `19201dc` — chore(dashboard): refresh state 2026-05-03T07:08:39Z · 11h ago
- `56dfd8d` — chore(dashboard): refresh state 2026-05-03T04:29:53Z · 13h ago
- `7595bbf` — chore(dashboard): refresh state 2026-05-03T00:10:25Z · 18h ago

## CDN probes

- OK  `jsdelivr` — 200 · 161ms
- OK  `rawGithub` — 200 · 226ms
- OK  `everyayah` — 200 · 569ms
- OK  `quranicaudio` — 200 · 296ms
- OK  `qurancdn` — 200 · 284ms

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
