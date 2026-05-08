# deen.in — operations status

_Last refresh: 2026-05-08T16:00:36.013Z (just now)_
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 8 events · 6 users · last 3d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 6 events · 4 users · last 7d ago
- REACT-NATIVE-6 — App Hanging: App hanging for at least 2000 ms. · 1 events · 1 users · last 20h ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 22d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 59
- `Application Opened` — 33
- `Application Became Active` — 28
- `Application Installed` — 3

## GitHub — recent commits to main

- `434cfc0` — chore(dashboard): refresh state 2026-05-08T14:02:40Z · 2h ago
- `8969318` — chore(dashboard): refresh state 2026-05-08T11:55:51Z · 4h ago
- `a488592` — chore(dashboard): refresh state 2026-05-08T10:06:02Z · 6h ago
- `e1e7c8b` — chore(dashboard): refresh state 2026-05-08T08:24:38Z · 8h ago
- `ce7308a` — chore(dashboard): refresh state 2026-05-08T06:55:23Z · 9h ago
- `e5c9f3a` — chore(dashboard): refresh state 2026-05-08T04:40:37Z · 11h ago
- `e1f1304` — chore(dashboard): refresh state 2026-05-08T01:21:02Z · 15h ago
- `22b2610` — chore(dashboard): refresh state 2026-05-07T23:29:28Z · 17h ago
- `c6376d1` — chore(dashboard): refresh state 2026-05-07T22:06:07Z · 18h ago
- `e5f548d` — chore(dashboard): refresh state 2026-05-07T20:49:34Z · 19h ago

## CDN probes

- OK  `jsdelivr` — 200 · 105ms
- OK  `rawGithub` — 200 · 182ms
- OK  `everyayah` — 200 · 736ms
- OK  `quranicaudio` — 200 · 178ms
- OK  `qurancdn` — 200 · 208ms

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
