# deen.in — operations status

_Last refresh: 2026-05-06T13:18:15.734Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **—** |
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

_Sentry pull failed: The operation was aborted due to timeout_

## PostHog — top events (24h)

- `Application Backgrounded` — 52
- `Application Opened` — 27
- `Application Became Active` — 24
- `Application Installed` — 4

## GitHub — recent commits to main

- `13cf5ac` — chore(dashboard): refresh state 2026-05-06T11:27:22Z · 2h ago
- `1fe2fbe` — chore(dashboard): refresh state 2026-05-06T09:29:02Z · 4h ago
- `9614147` — chore(dashboard): refresh state 2026-05-06T06:35:18Z · 7h ago
- `a8ec538` — chore(dashboard): refresh state 2026-05-06T03:39:40Z · 10h ago
- `6eaa0ce` — chore(dashboard): refresh state 2026-05-05T23:55:05Z · 13h ago
- `43fa952` — chore(dashboard): refresh state 2026-05-05T22:32:49Z · 15h ago
- `6c3f412` — chore(dashboard): refresh state 2026-05-05T21:12:12Z · 16h ago
- `98187e0` — chore(dashboard): refresh state 2026-05-05T19:58:56Z · 17h ago
- `9adb6b7` — chore(dashboard): refresh state 2026-05-05T18:02:02Z · 19h ago
- `dd65bcb` — chore(dashboard): refresh state 2026-05-05T16:34:53Z · 21h ago

## CDN probes

- OK  `jsdelivr` — 200 · 160ms
- OK  `rawGithub` — 200 · 355ms
- OK  `everyayah` — 200 · 571ms
- OK  `quranicaudio` — 200 · 238ms
- OK  `qurancdn` — 200 · 227ms

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

## Refresh errors

- **sentry** — The operation was aborted due to timeout
