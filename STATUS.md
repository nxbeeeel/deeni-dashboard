# deen.in — operations status

_Last refresh: 2026-04-29T21:12:57.061Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **100.00%** |
| DAU | **12** |
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 6 events · 5 users · last 4d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 2 events · 2 users · last 6d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 14d ago
- REACT-NATIVE-2 — ApplicationNotResponding: ANR · 1 events · 1 users · last 25d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 45
- `Application Opened` — 28
- `Application Became Active` — 22
- `Application Installed` — 3
- `Application Updated` — 1

## GitHub — recent commits to main

- `e6ac58f` — chore(dashboard): refresh state 2026-04-29T19:45:09Z · 1h ago
- `58a1254` — chore(dashboard): refresh state 2026-04-29T17:43:59Z · 3h ago
- `e5c9484` — chore(dashboard): refresh state 2026-04-29T15:34:17Z · 6h ago
- `ef168c9` — chore(dashboard): refresh state 2026-04-29T13:10:08Z · 8h ago
- `8b657d4` — chore(dashboard): refresh state 2026-04-29T11:16:58Z · 10h ago
- `46d1a7a` — chore(dashboard): refresh state 2026-04-29T09:14:03Z · 12h ago
- `4b2350e` — chore(dashboard): refresh state 2026-04-29T06:31:20Z · 15h ago
- `50d6fc1` — chore(dashboard): refresh state 2026-04-29T03:57:09Z · 17h ago
- `87c4593` — chore(dashboard): refresh state 2026-04-28T23:59:32Z · 21h ago
- `a0ecf68` — chore(dashboard): refresh state 2026-04-28T22:33:29Z · 23h ago

## CDN probes

- OK  `jsdelivr` — 200 · 333ms
- OK  `rawGithub` — 200 · 238ms
- OK  `everyayah` — 200 · 569ms
- OK  `quranicaudio` — 200 · 472ms
- OK  `qurancdn` — 200 · 468ms

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
