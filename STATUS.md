# deen.in — operations status

_Last refresh: 2026-04-28T22:33:27.877Z (just now)_
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 6 events · 5 users · last 3d ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 2 events · 2 users · last 5d ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 13d ago
- REACT-NATIVE-2 — ApplicationNotResponding: ANR · 1 events · 1 users · last 24d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 61
- `Application Became Active` — 32
- `Application Opened` — 27
- `Application Installed` — 1

## GitHub — recent commits to main

- `25a6b6f` — chore(dashboard): refresh state 2026-04-28T21:14:09Z · 1h ago
- `7ee1549` — feat(dashboard): field notes — log user-reported issues via Telegram · 1h ago
- `0848f84` — chore(dashboard): refresh state 2026-04-28T21:12:33Z · 1h ago
- `008699c` — chore(dashboard): refresh state 2026-04-28T21:05:14Z · 1h ago
- `4325753` — chore(dashboard): refresh state 2026-04-28T21:00:47Z · 2h ago
- `773784e` — chore(dashboard): refresh state 2026-04-28T20:55:08Z · 2h ago
- `960969c` — fix(dashboard): add set -x diagnostics to git steps; EAS auth-only errors · 2h ago
- `ca4852a` — chore(dashboard): refresh state 2026-04-28T20:53:53Z · 2h ago
- `afb13d5` — chore(dashboard): refresh state 2026-04-28T20:49:17Z · 2h ago
- `72b7671` — fix(dashboard): bulletproof commit step with cp/hard-reset; treat EAS no-updates as healthy · 2h ago

## CDN probes

- OK  `jsdelivr` — 200 · 552ms
- OK  `rawGithub` — 200 · 297ms
- OK  `everyayah` — 200 · 535ms
- OK  `quranicaudio` — 200 · 392ms
- OK  `qurancdn` — 200 · 332ms

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
