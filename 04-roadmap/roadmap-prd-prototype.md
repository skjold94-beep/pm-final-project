# Feature Roadmap, Module 4 · RouteLogic Velocity

**Team:** 2 engineers + 1 designer + 1 CS lead

## Strategic anchors
- **Persona:** The Frontline Driver: runs dozens of stops a day, often one-handed, outdoors and against the clock, on routes with unreliable signal
- **Primary metric:** Doorstep in-app confirmation rate: % of stops confirmed in RouteLogic with a successfully uploaded POD photo within 2 min of arrival (baseline ≤65% → target ≥90%)
- **Moment of misery:** Confirming a delivery takes “three screens, in the rain, at a doorstep, with a package in one hand”, and ~35% of POD photos fail silently, so drivers text dispatch and retake photos instead (UXR-01, UXR-07)
- **Guardrail:** Manager Compliance CSAT stays ≥3.9. Also track compliance record completeness: the share of stops with all required fields and a POD attached.

## Scoring
| Feature | Value | Effort | Quadrant | Decision | Rationale |
|---|---|---|---|---|---|
| B1 One-Click Compliance Checklist | 3 | 3 | Time Sinker | Next | It cuts into the 14.6-min coordinator step and helps the completeness guardrail. But it only works once drivers confirm deliveries in the app, so it depends on the primary metric moving first. |
| B2 Smart Daily Report Auto-Fill | 1 | 4 | Time Sinker | Cut | This is AI reporting for managers, who already rate Reporting 4.5. It’s what Sales and Engineering want, not what the driver needs. |
| B3 Shift Handoff Wizard | 2 | 3 | Time Sinker | Later | It saves coordinators a real 6.8 min/day, but it’s the wrong persona. Your M3 notes say Scheduling has no research behind it yet, so it belongs in discovery, not the build. |
| B4 Mobile-First Coordinator Dashboard | 2 | 5 | Time Sinker | Cut | It’s the biggest build on the list and it’s for the wrong persona. It also redesigns Core Dispatch, which drivers rate 4.3. |
| B5 Step Progress Indicator | 1 | 1 | Fill-In | Later | It’s a cosmetic coordinator change with no link to the doorstep. Only worth doing if the designer has spare time. |
| B6 Driver Alert Notifications | 4 | 2 | Quick Win | Now | It’s the only feature for drivers. Limited to a “POD didn’t upload, retake now” alert, it ends the silent failure behind the 35% of photos that fail. It can’t be a 5 because it reports the failure without cutting the three screens. |
| B7 Contextual AI ETA Display | 1 | 3 | Time Sinker | Cut | Only 11% use it, it has nothing to do with confirming a delivery, and AI work is a poor use of 2 engineers for a 4-week pilot. |
| B8 Fleet Analytics Manager View | 1 | 4 | Time Sinker | Cut | It’s an exec dashboard for the happiest group (Reporting 4.5) and does nothing for the driver. |
| B9 Compliance Audit Trail Export | 2 | 2 | Fill-In | Later | It protects the Manager CSAT guardrail, but none of the 3 pilot accounts needs an audit within 4 weeks. Do it after the pilot. |
| B10 In-App Coordinator Training | 5 | 3 | Major Project | Next | It’s the wrong persona. Your CS lead can onboard the pilot accounts by hand, with no engineering time. |

## Roadmap
### NOW, Pilot (4 weeks, 3 accounts)
- **B6 Driver Alert Notifications**, It’s the only feature for drivers. Limited to a “POD didn’t upload, retake now” alert, it ends the silent failure behind the 35% of photos that fail. It can’t be a 5 because it reports the failure without cutting the three screens.

### NEXT, GA Release (weeks 5-8)
- **B1 One-Click Compliance Checklist**, It cuts into the 14.6-min coordinator step and helps the completeness guardrail. But it only works once drivers confirm deliveries in the app, so it depends on the primary metric moving first.
- **B10 In-App Coordinator Training**, It’s the wrong persona. Your CS lead can onboard the pilot accounts by hand, with no engineering time.

### LATER, backlog
- **B3 Shift Handoff Wizard**, It saves coordinators a real 6.8 min/day, but it’s the wrong persona. Your M3 notes say Scheduling has no research behind it yet, so it belongs in discovery, not the build.
- **B5 Step Progress Indicator**, It’s a cosmetic coordinator change with no link to the doorstep. Only worth doing if the designer has spare time.
- **B9 Compliance Audit Trail Export**, It protects the Manager CSAT guardrail, but none of the 3 pilot accounts needs an audit within 4 weeks. Do it after the pilot.

### ✂ Cut List
- **B2 Smart Daily Report Auto-Fill**, This is AI reporting for managers, who already rate Reporting 4.5. It’s what Sales and Engineering want, not what the driver needs.
- **B4 Mobile-First Coordinator Dashboard**, It’s the biggest build on the list and it’s for the wrong persona. It also redesigns Core Dispatch, which drivers rate 4.3.
- **B7 Contextual AI ETA Display**, Only 11% use it, it has nothing to do with confirming a delivery, and AI work is a poor use of 2 engineers for a 4-week pilot.
- **B8 Fleet Analytics Manager View**, It’s an exec dashboard for the happiest group (Reporting 4.5) and does nothing for the driver.
