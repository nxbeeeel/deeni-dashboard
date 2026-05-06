# deen.in — operations status

_Last refresh: 2026-05-06T22:26:31.349Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **100.00%** |
| DAU | **13** |
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 8 events · 6 users · last 2d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 6 events · 4 users · last 5d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 21d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 65
- `Application Became Active` — 39
- `Application Opened` — 29
- `Application Installed` — 4

## GitHub — recent commits to main

- `5ec91c7` — chore(dashboard): refresh state 2026-05-06T21:16:00Z · 1h ago
- `c5ae8d6` — chore(dashboard): refresh state 2026-05-06T19:53:30Z · 3h ago
- `6d82fb9` — chore(dashboard): refresh state 2026-05-06T17:46:54Z · 5h ago
- `8de40f3` — chore(dashboard): refresh state 2026-05-06T15:42:52Z · 7h ago
- `f9b4380` — chore(dashboard): refresh state 2026-05-06T13:18:16Z · 9h ago
- `13cf5ac` — chore(dashboard): refresh state 2026-05-06T11:27:22Z · 11h ago
- `1fe2fbe` — chore(dashboard): refresh state 2026-05-06T09:29:02Z · 13h ago
- `9614147` — chore(dashboard): refresh state 2026-05-06T06:35:18Z · 16h ago
- `a8ec538` — chore(dashboard): refresh state 2026-05-06T03:39:40Z · 19h ago
- `6eaa0ce` — chore(dashboard): refresh state 2026-05-05T23:55:05Z · 23h ago

## CDN probes

- OK  `jsdelivr` — 200 · 111ms
- OK  `rawGithub` — 200 · 152ms
- OK  `everyayah` — 200 · 574ms
- OK  `quranicaudio` — 200 · 440ms
- OK  `qurancdn` — 200 · 614ms

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
