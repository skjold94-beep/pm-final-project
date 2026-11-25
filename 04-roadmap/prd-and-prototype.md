# B6 Driver Alert Notifications: “POD didn’t upload, retake now” alert, Simplified PRD (RouteLogic)

**Author:** Me · **Status:** Draft · **Target:** High-Fidelity Prototype · **Persona:** The Frontline Driver: runs dozens of stops a day, often one-handed, outdoors and against the clock, on routes with unreliable signal (UXR-01, UXR-06, UXR-11)

## 1. The Big Picture
- **Vision:** To eliminate silent proof-of-delivery failures by telling drivers at the doorstep, within seconds, whether their photo uploaded, and giving them a one-tap retry when it didn’t.
- **Press release:** Today, RouteLogic launched Velocity Driver Alerts, an instant upload check for proof-of-delivery photos. Until now, about 1 in 3 POD photos failed silently on weak signal. Drivers working one-handed in the rain had no idea whether a photo had arrived, so they retook it “three times”, or gave up and texted the dispatcher. Each of those deliveries ended up in a chat thread instead of the system of record, and coordinators spent their afternoons rebuilding compliance records by hand.

Now, the moment a photo fails, the driver gets an alert with vibration and sound, and can retry with one tap without leaving the stop screen. When the upload succeeds, a clear “✓ Uploaded” tells them they’re done and can drive on. Drivers leave every stop knowing their work is recorded, and dispatchers stop getting “delivered” texts. The 4-week pilot with 3 accounts aims to raise the share of stops confirmed in the app, with a successful POD, from about 65% to 90% or more.
- **Success metric:** Doorstep in-app confirmation rate: % of stops with a successfully uploaded POD within 2 min of arrival (≤65% → ≥90%)
- **Guardrail:** Manager Compliance CSAT ≥3.9 and compliance record completeness held or improved

## 2. The Details
### User stories
- As a Frontline Driver, I want to know within seconds if my POD photo failed to upload, so that I don't leave the doorstep with the delivery unrecorded.
- As a Frontline Driver, I want to retry a failed upload with one tap without leaving the stop screen, so that I can fix it one-handed with a package in my other hand.
- As a Frontline Driver, I want a clear "✓ Uploaded" confirmation, so that I stop retaking photos and texting dispatch "just in case".
- As a Frontline Driver, I want the alert to vibrate and make a sound, so that I notice it outdoors even when I'm not looking at the screen.
- As a Coordinator, I want stops with no POD after 2 minutes flagged to me, so that I don't have to rebuild compliance records by hand at the end of the day.
### Screens to build
- 1. Stop screen (entry point): current stop address, recipient, and a large "Take POD photo" button usable with one thumb, plus a simulated signal toggle (Strong / Weak / None) for the demo.
- 2. Upload status (feature core): photo thumbnail with a live status of Uploading… → Failed. On failure, a full-width red alert banner "Photo didn't upload – retry" with a large one-tap Retry button and a vibration/sound cue, all without leaving the stop.
- 3. Delivery confirmed (success): big green "✓ Uploaded" with timestamp and time-from-arrival (e.g. "Confirmed in 0:48"), and a "Next stop" button.
### Functional requirements
- - The system must show the upload status (Uploading / Failed / Uploaded) within 1 second of the photo being taken.
- - The system must treat an upload with no success response within 10 seconds as Failed. No upload may stay "Uploading" with no result.
- - The system must show the failure alert on the current stop screen, with no navigation required.
- - The system must provide a Retry button at least 56px tall, reachable with one thumb in the bottom third of the screen.
- - The system must show "✓ Uploaded" only after a confirmed success, never optimistically.
- - The system must log, for each stop: arrival time, each upload attempt and its result, and the final upload time.
- - The system must calculate and show whether the stop was confirmed within 2 minutes of arrival.
- - The system must keep the "Next stop" button visible but marked "POD missing" until an upload succeeds, so the driver is warned but never blocked.
### Smart behaviors (Situation → Outcome)
- If an upload fails or times out → show the red alert banner, vibrate, play a sound, and show a one-tap Retry.
- If the driver taps Retry and signal is still "None" → keep the photo on the device, show "Saved – will upload when signal returns", and retry automatically when the signal toggle changes.
- If an upload succeeds → show "✓ Uploaded" with the time since arrival, and hide the retake option.
- If 2 minutes pass since arrival with no successful POD → mark the stop "Flagged for coordinator" in the log.
- If the driver taps "Next stop" without a successful POD → show a one-line warning ("POD not uploaded – continue anyway?") and let them continue, keeping the stop flagged.
- If 3 retries fail in a row → stop prompting and switch to automatic background retry, so the driver isn't stuck at the door.
### Technical constraints
- Single-file React app; useState/useReducer only, no external state library.
- No real camera, network, or upload API: simulate photo capture with a placeholder image and simulate upload results from the signal toggle (Strong = success in 1s, Weak = 50% fail after 3s, None = fail after 10s timeout).
- No backend, no database, no authentication; the event log lives in memory and is shown in a collapsible debug panel.
- Mobile-first layout (375px wide), large touch targets, high contrast for outdoor use.
- Vibration through navigator.vibrate if available, otherwise skip silently; sound through a short Web Audio beep.
- Don't build: route list, map, the three-screen confirmation flow, coordinator dashboard, SMS/email alerts, or AI photo checks.

## 3. The Logistics
### Features out
- No one-tap delivery confirmation redesign (the three-screen flow stays as it is)
- No full offline mode for the route or stop list
- No SMS or email alerts
- No AI photo-quality checks
- No manager or coordinator alert dashboard
- No route-change or compliance-field push alerts
- No login, settings, map, or route history
### Edge cases & safety guard
- No signal at all → save the photo on the device, show "Saved – will upload when signal returns", and retry automatically
- Weak signal / slow upload → show "Uploading…" for up to 10s, then mark it Failed. Never leave it spinning forever
- Upload succeeds after it was marked Failed → switch to "✓ Uploaded" and clear the alert, without creating a duplicate POD
- Driver retakes the photo during a retry → keep only the latest photo and cancel the earlier upload
- 3 retries fail in a row → stop prompting and switch to background retry, so the driver can move on
- Driver leaves the stop without a POD → warn once and let them continue, but keep the stop flagged
- Phone on silent / vibration not supported → still show the visual banner and skip the cue quietly
- Safety: never show "✓ Uploaded" without a confirmed success; never block the driver from moving to the next stop; never discard a photo before it has uploaded; never send more than one alert per failure
### Decision log
- 1. Cut the one-tap delivery confirmation redesign to focus on silent POD failures. It addresses the "three screens" half of the misery, but it's a separate feature too big for 2 engineers in a 4-week pilot. Fixing silent failures moves the primary metric fastest with the least build.
- 2. Made the alert warn rather than block: the driver can always move to the next stop without a POD. Drivers are against the clock, and a hard block at the doorstep would push them back to texting dispatch, the exact workaround we're trying to remove.
### Evals
- Accuracy: ≥99% of uploads show the correct final status (Uploaded vs Failed), with 0 false "✓ Uploaded" in test runs across Strong / Weak / None signal
- Time-on-task: the failure alert appears ≤3s after a failure or 10s timeout, and a stop goes from arrival to a confirmed POD in ≤2 min in ≥90% of pilot stops
- Safety: 0 photos lost before upload and 0 cases of the driver being blocked from the next stop; no more than one alert per failure

## MoSCoW scope
- **Must:** 1. Detect a failed or timed-out POD upload on the device. This is the whole point: about 35% of photos fail with no error today (UXR-07).; 2. In-app alert at the doorstep within seconds: “Photo didn’t upload – retry”. The driver has to find out before leaving the stop, not afterwards.; 3. One-tap retry from the alert, without leaving the stop screen. The driver has one hand free and a package in the other, so the fix can’t add screens.; 4. Clear “✓ Uploaded” confirmation. Without a success signal, drivers keep retaking photos “three times” even when the upload worked.; 5. Log each stop’s upload result and time from arrival to upload. Without this, the pilot can’t measure the doorstep in-app confirmation rate (≤65% → ≥90%).
- **Should:** 1. Keep the photo on the phone and retry automatically when signal returns. On dead signal a manual retry fails again, so this protects the 2-minute target. Of everything here, it’s the most likely item to become a Must if pilot data shows repeat failures.; 2. Vibration and sound with the alert. Drivers are outdoors, in the rain, with the phone in a pocket or mount, so they may not see a visual alert.; 3. Flag the stop to the coordinator if there’s no POD 2 minutes after arrival. This protects the compliance-completeness guardrail, but the driver can succeed without it.
- **Could:** 1. Push alerts on route changes. Useful for the 8–15 min delay (UXR-02), but it doesn’t move the doorstep confirmation rate.; 2. Alerts when a required compliance field is missing. Same alert system, but a different problem.; 3. Warn about weak signal before the photo is taken. It’s a nice extra, and the Should-have auto-retry already covers most of the same need.
- **Won't (now):** 1. Cutting three-screen confirmation down to one tap. It’s the real fix for the “three screens” half of the misery, but it’s its own feature and too big alongside this one in 4 weeks.; 2. Full offline mode for the route and stop list. That’s a separate reliability problem (UXR-06) and a large build.; 3. Alerts by SMS or email. The aim is to keep drivers in the app, not push them back to texting.; 4. AI checks on photo quality. It’s not part of the failure drivers have, and AI work is a poor use of 2 engineers.; 5. Alert dashboards for managers or coordinators. It’s the wrong persona, and managers are already happy with Reporting (4.5).

---
**Builder hook:** Build a working prototype based on this PRD. Use the User Story as the core flow, Functional Requirements as build constraints, and prioritize speed and clarity over visual complexity.
