# deen.in — operations status

_Last refresh: 2026-05-01T18:40:41.382Z (just now)_
_App version: 1.5.0 (build 49)_

## Headline

| | |
|--|--|
| Crash-free (24h) | **100.00%** |
| DAU | **16** |
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

- REACT-NATIVE-3 — Error: Call to function 'ExpoLocation.removeWatchAsync' has been rejected. · 7 events · 5 users · last 11h ago
- REACT-NATIVE-5 — Error: Call to function 'NativeDatabase.prepareSync' has been rejected. · 4 events · 3 users · last 9h ago
- REACT-NATIVE-4 — RuntimeException: android.os.DeadSystemException · 1 events · 1 users · last 15d ago
- REACT-NATIVE-2 — ApplicationNotResponding: ANR · 1 events · 1 users · last 27d ago

## PostHog — top events (24h)

- `Application Backgrounded` — 159
- `Application Became Active` — 102
- `Application Opened` — 51
- `Application Installed` — 7

## GitHub — recent commits to main

- `256550c` — chore(dashboard): refresh state 2026-05-01T17:03:25Z · 2h ago
- `068d21c` — chore(dashboard): refresh state 2026-05-01T15:34:16Z · 3h ago
- `10b06c3` — chore(dashboard): refresh state 2026-05-01T14:02:15Z · 5h ago
- `a73ed84` — chore(dashboard): refresh state 2026-05-01T12:02:56Z · 7h ago
- `479fad9` — chore(dashboard): refresh state 2026-05-01T10:54:12Z · 8h ago
- `88bef8d` — chore(dashboard): refresh state 2026-05-01T09:17:54Z · 9h ago
- `2de2075` — chore(dashboard): refresh state 2026-05-01T07:15:22Z · 11h ago
- `c9f3945` — chore(dashboard): refresh state 2026-05-01T04:10:52Z · 15h ago
- `9afa2fa` — chore(dashboard): refresh state 2026-04-30T23:59:31Z · 19h ago
- `6733b50` — chore(dashboard): refresh state 2026-04-30T22:58:11Z · 20h ago

## CDN probes

- OK  `jsdelivr` — 200 · 243ms
- OK  `rawGithub` — 200 · 375ms
- OK  `everyayah` — 200 · 562ms
- OK  `quranicaudio` — 200 · 309ms
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
