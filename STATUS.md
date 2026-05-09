# deen.in — operations status

_Last refresh: 2026-05-09T01:19:07.112Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **—** |
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

_Sentry pull failed: The operation was aborted due to timeout_

## PostHog — top events (24h)

- `Application Backgrounded` — 46
- `Application Opened` — 25
- `Application Became Active` — 23
- `Application Installed` — 2

## GitHub — recent commits to main

- `01b173f` — chore(dashboard): refresh state 2026-05-08T23:30:47Z · 2h ago
- `0993410` — chore(dashboard): refresh state 2026-05-08T22:02:52Z · 3h ago
- `53c34c9` — chore(dashboard): refresh state 2026-05-08T20:36:31Z · 5h ago
- `25a85e1` — chore(dashboard): refresh state 2026-05-08T19:27:11Z · 6h ago
- `c37d027` — chore(dashboard): refresh state 2026-05-08T17:42:04Z · 8h ago
- `dea0bfc` — chore(dashboard): refresh state 2026-05-08T16:00:36Z · 9h ago
- `434cfc0` — chore(dashboard): refresh state 2026-05-08T14:02:40Z · 11h ago
- `8969318` — chore(dashboard): refresh state 2026-05-08T11:55:51Z · 13h ago
- `a488592` — chore(dashboard): refresh state 2026-05-08T10:06:02Z · 15h ago
- `e1e7c8b` — chore(dashboard): refresh state 2026-05-08T08:24:38Z · 17h ago

## CDN probes

- OK  `jsdelivr` — 200 · 502ms
- OK  `rawGithub` — 200 · 305ms
- OK  `everyayah` — 200 · 571ms
- OK  `quranicaudio` — 200 · 404ms
- OK  `qurancdn` — 200 · 347ms

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
