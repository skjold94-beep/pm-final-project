# Hypothesis & Success Metrics (Module 3)

## Pre-work · Hypothesis check
- **Role , who you are solving for (from M2):** The frontline delivery driver. They run dozens of stops a day, often one-handed, outdoors and against the clock, on routes where they can’t count on having signal (UXR-01, UXR-06, UXR-11).
- **Goal , what this user is ultimately trying to achieve:** To get through each stop quickly, and to trust the app to hold their route and record their work from the first stop to the last.
- **Friction / moment of misery , the specific pain blocking their goal:** The app crashes partway through a route and the remaining stops disappear. The driver can’t recover alone. They have to stop and call the office to have their own route read back to them: “Twenty minutes gone” (Elena, UXR-03). BUG-2031 (Critical) confirms crashes on Android 12/13 once a route passes about 40 stops. The app is also too heavy for daily use. Marking a stop delivered takes three screens (UXR-01), “Start Route” is buried (UXR-11), about 35% of proof-of-delivery photos fail without any error (UXR-07), and route changes arrive 8–15 minutes late (UXR-02).
- **Current workaround , the external tool or manual process they rely on (M2):** Drivers build backups outside the app every day:

They screenshot the stop list each morning while they still have signal (UXR-06).
5 of 7 carry a paper manifest “just in case the app dies” (UXR-12).
They text the dispatcher instead of marking stops delivered in the app (UXR-01).
They call the office to rebuild a lost route or to get changes faster (UXR-02, UXR-03).
Dispatch posts live route changes in a WhatsApp group.
- **Problem Hook , your one-sentence framing of the business crisis (M1):** “RouteLogic has become too heavy for the people who run fleets in real time, and our biggest customer is already trialing the alternative.”
- **Value Proposition , the outcome your initiative promised to deliver (M1):** RouteLogic Velocity gives frontline teams a fast, focused workspace for the jobs they do every hour (track, reassign, communicate) with no enterprise clutter in the way. Advanced capabilities like compliance and financial reporting stay fully available, but move into dedicated spaces for the people who need them. Why now: the largest account is already evaluating a leaner competitor, frontline usage is falling, and every month of waiting makes the “complex” label harder to shake.

## Read your data snapshots
- **Does the funnel data confirm your M2 friction point, or does it tell a different story? Note where the numbers align with the qualitative pain you found and where they diverge.:** _(not filled in)_
- **Do the retention patterns align with the workaround your M2 persona used to find content? Note what the Mo. 0→1 drop suggests about the onboarding experience your persona described as frustrating.:** _(not filled in)_
- **Does the LTV gap and the content mix (61% trending for Wanderers) confirm the moment of misery your persona described? Note which segment your persona is in and whether the data confirms their pain.:** _(not filled in)_
- **Does the low adoption confirm your persona is burdened by tools they don’t use? Note whether the low scheduling adoption (42%) for coordinators matches your M2 moment of misery.:** In general, low adoption does not always tie to "not using the product". Because some features are meant for the different personas, and not everyone across the board. 

Though, it is frigthening that coordinations are not actively using the Shift Scheduling Module, because it is meant for coordinaters and not just managers. It does tie to some frustrations mentioned earlier. 

Though, Shift Scheduling is more of a new area, which was not covered previously. It still ties to underused areas.

the numbers support your Velocity bet. The features with the most friction are the ones frontline users rely on most (Dispatch Board, Optimizer, Compliance), and the manager-only features are noise for them. The numbers add nuance in one place: the frontline problem looks less like “too many features” and more like the core features being unreliable under real field conditions.
- **Does the workflow data match the manual process or hack you documented in M2? Note whether the specific drop-offs or time gaps explain why your persona avoids the digital tool.:** My M2 persona is the driver, and this snapshot measures coordinators, so it can’t directly prove the driver workarounds (screenshots, paper manifests, texting deliveries). It does closely match the dispatcher moment of misery from M1: dispatchers make the decision outside RouteLogic (calls, Google Maps, spreadsheets, WhatsApp) and only update the tool afterwards for compliance.

Compliance is where the tool breaks down. Log Compliance Checks takes 14.6 min against a 3-min benchmark (+11.6 min), and only 48% of coordinators get that far. In M1 I described RouteLogic as “the system they update afterwards for compliance, not the tool they use to make the decision”. The data shows even that after-the-fact logging is too slow, so many coordinators never finish it.

Route assignment is slow enough to push people outside the tool. Assigning routes via the Optimizer takes 8.2 min against 4.0, and 29% drop off before reaching it. That fits coordinators reassigning by phone and WhatsApp in a live disruption instead of clicking through menus. It also links to my M2 finding that drivers override the optimised route every day (UXR-05), because a slow tool and an untrusted output are both reasons to bypass it.

Therefore, the cost adds up. The time gaps total about 30 min a day (0.5 + 4.2 + 11.6 + 6.8 + 6.7), which lines up with the 31 minutes of daily waste in the NPS data.
- **Look at the CSAT heatmap. Which specific cell most directly maps to your persona’s friction? Note how the NPS trend justifies the urgency of your M1 Problem Hook.:** Cell: Drivers × Compliance (2.8, Weak).

For my driver persona, the closest cell is the delivery-confirmation and proof-of-delivery flow, which I’m treating as the compliance side of the driver’s job:

Marking a stop delivered takes three screens, so drivers text the dispatcher instead (UXR-01, BUG-2055).
About 35% of POD photos fail on weak signal without any error, so drivers retake them up to three times (UXR-07, BUG-2061).

Both are compliance steps the driver is required to do, and both fail in exactly the doorstep conditions I documented. The matching coordinator cell, Coordinators × Compliance (2.2), is the lowest frontline score outside Reporting. It lines up with Snapshot 2 (14.6 min against a 3-min benchmark) and with my M1 dispatcher misery of “updating RouteLogic afterwards for compliance”.

Adding more info & nuances: 
Drivers rate Core Dispatch at 4.3 (Strong), even though my core moment of misery, the mid-route crash that loses stops (BUG-2031), sits in that area. My understanding is that drivers value the core dispatch features when they work, and the crash is a severe but intermittent failure, mainly on Android 12/13 routes over 40 stops. An average score can hide that. So the crash is a reliability fix inside a well-liked feature, not a reason to redesign it. Drivers × Scheduling (1.9, Critical) isn’t covered by my research, so I’m noting it as a gap to explore.

I’d set aside the Drivers × Reporting score (1.1). Only 3% of drivers use Reporting, so that score mostly measures clutter in their view, not a failed workflow.

NPS Trend justifying M1 urgency:
My problemhook said RouteLogic “has become too heavy for the people who run fleets in real time, and our biggest customer is already trialing the alternative.” The data backs every part of that:
- Coordinator NPS fell 30 points, from +18 to −12. The people running fleets in real time have gone from promoters to detractors.
- Daily time lost to workarounds rose from about 9 to 31 minutes (3.4×). The calls, WhatsApp groups and spreadsheets I documented are growing, not stable.
- 4 of 5 churning accounts now cite complexity, up from 1 of 8. “Too heavy” has become the main reason accounts leave, which makes the risk to the largest account concrete rather than speculative.
- Managers are satisfied (Reporting 4.5, Compliance 3.9) while the frontline struggles. That is the split Velocity is designed around: keep manager power in its own space and make the frontline fast.

Ergo, the Velocity pilot’s +34% route-assignment speed is early evidence that the fix works. Every month of delay adds more workaround time and makes the “complex” label harder to undo.


Pivot check:
Is Velocity targeting the most critical pain point? Not as currently scoped. Velocity is framed as a fast workspace for “track, reassign, communicate”, with compliance moved into a separate space. The data says compliance is part of the frontline job, not just a manager concern. If it’s simply moved elsewhere, the biggest pain stays.

The pivot: keep the persona and the core bet, and change the focus:

Build compliance into the workflow instead of moving it out. For drivers, one-tap delivery with POD photos that confirm the upload completes the compliance record at the doorstep. For coordinators, compliance data is captured automatically from dispatch actions. The target is getting coordinator compliance time from 14.6 to about 3 min, and Driver × Compliance CSAT above 3.5.
Protect Core Dispatch, don’t redesign it. Fix the crash and offline reliability, but leave a 4.3 feature mostly alone.
Put Scheduling next, starting with coordinator shift handoff. Explore it in discovery first, because I have no research on it yet.
Leave Reporting and AI for now. Separating them from frontline views is enough.

## Step 3 · Craft your hypothesis
- **Qualitative evidence (from M2) , quote the specific friction / moment of misery for your persona:** Marking a stop delivered takes “three screens, in the rain, at a doorstep, with a package in one hand.” (Driver, UXR-01, BUG-2055)

Instead, drivers text the dispatcher to report the delivery, so the record ends up in a chat thread rather than in RouteLogic. Proof of delivery has the same problem: about 35% of POD photos fail on weak signal without any error, so drivers take them “three times” and still leave unsure whether any arrived (UXR-07, BUG-2061).
- **Quantitative evidence (from M3) , name the metric or data point that confirms the pain; cite the number:** Compliance CSAT is weak for both frontline roles, even though most of them use it. Drivers rate it 2.8/5 at 64% adoption, and coordinators rate it 2.2/5 at 77% adoption (Snapshot 3; adoption from the feature table).

On the coordinator side, Log Compliance Checks takes 14.6 min against a 3-min benchmark (+11.6 min, almost 5× longer), and only 48% of coordinators get that far in the daily workflow (Snapshot 2). That is the largest single contributor to the 31 min a day lost to manual workarounds, up from about 9 min two years ago. Over the same period, coordinator NPS has dropped from +18 to −12 (Snapshot 3).
- **Persona , role, goal, and the friction you confirmed in the reconciliation steps:** Role: a frontline delivery driver. They run dozens of stops a day, often one-handed, outdoors and against the clock, on routes with unreliable signal (UXR-01, UXR-06, UXR-11).

Goal: to get through each stop quickly and trust that the app holds their route and records their work, from the first stop to the last.

Confirmed friction: the delivery and compliance step at the doorstep. Confirming a stop takes three screens, and about 35% of POD photos fail without any error. So drivers report deliveries by text and retake photos, and the work happens outside RouteLogic (UXR-01, UXR-07). The data confirmed this:
- Driver × Compliance CSAT is 2.8/5 at 64% adoption.
- Downstream, coordinators then spend 14.6 min a day logging compliance against a 3-min benchmark.

The reconciliation changed the focus. The mid-route crash (UXR-03) is still a serious reliability fix, but it sits in Core Dispatch, which drivers rate 4.3. So it is no longer the main friction this initiative targets.
- **Problem you are solving , one sentence describing the specific friction this initiative removes:** Drivers can’t record a delivery and its proof in RouteLogic quickly or reliably: it takes three screens, and photos fail silently about 35% of the time on weak signal. So they report deliveries by text, and coordinators spend 14.6 minutes a day piecing compliance records back together by hand.
- **Strategic outcome , what behaviour change do you expect, and how does it map to retention / revenue / churn?:** Drivers and coordinators complete delivery compliance inside RouteLogic instead of by text and by hand. That cuts daily workaround time and restores frontline NPS, which directly reduces the complexity-driven churn that puts our largest account’s renewal at risk

Expected behaviour change:
- Drivers confirm deliveries and proof of delivery in the app at the doorstep, instead of texting the dispatcher and retaking photos. RouteLogic becomes where the work happens, not where it gets logged afterwards.
- Coordinators stop rebuilding compliance records by hand and finish their daily workflow inside RouteLogic. Completion past the compliance step should rise from 48% to 70% or more, and compliance logging should drop from 14.6 minutes toward the 3-minute benchmark.

How it maps to the business:
- Churn: 4 of 5 churning accounts now cite complexity as the reason, up from 1 of 8. Removing the frontline workflow with the most friction goes straight at the main churn driver.
- Retention: less daily workaround time (31 min, down toward the 9 min of two years ago) and better Compliance CSAT (2.8 rising to 3.5 or more) should reverse the coordinator NPS collapse (+18 to −12). The frontline turns from detractors back into advocates at renewal.
- Revenue: this protects the largest enterprise account, which is trialling a leaner competitor. It also gives sales evidence that RouteLogic is now both powerful and fast, which helps win back and keep mid-size fleets.
- **Primary success metric (initiative signal) , the leading indicator that tells you the gap is closing:** The doorstep in-app confirmation rate: the percentage of stops a driver confirms in RouteLogic, with a POD photo that uploads successfully, within 2 minutes of arriving at the stop.

- Why it’s a leading indicator: it moves as soon as drivers change behaviour, stop by stop, so you’d see it in the pilot within days. NPS, churn and renewals take months to react.
- Why it closes the gap: each stop confirmed in the app is one fewer text to the dispatcher and one fewer photo retake. It’s also one fewer compliance record a coordinator has to rebuild by hand, which is what feeds the 14.6-minute compliance time.
- Baseline: POD uploads currently succeed only about 65% of the time on weak signal (about 35% fail, UXR-07). The research doesn’t measure how many deliveries are confirmed in-app versus by text, so set the baseline in the first week of the pilot.
- Target: 90% or more of stops confirmed in-app with a successful POD by the end of the pilot.
- **Guardrail metric (product signal) , the metric that must NOT drop; it protects your existing base:** Manager Compliance CSAT must stay at 3.9 or higher (Snapshot 3).

- Why this metric: Velocity changes how compliance data is captured. It comes from one-tap doorstep confirmations and dispatch actions instead of manual coordinator entry. Managers are the existing base that relies on that data: 86% use Financial Reporting, and they rate Compliance 3.9 and Reporting 4.5. If a faster frontline flow produces thinner or less accurate compliance records, managers will notice first. They’re also the buyers who decide on renewals.
- What a drop would signal: the team made it faster for the frontline by losing audit quality. That trade would weaken RouteLogic’s position with compliance-heavy enterprise customers.
- How to track it alongside CSAT: monitor the compliance record completeness rate, meaning the share of stops with all required fields and a POD attached, as an objective data-quality check.
- **Decision window , how much time or data before you scale, pivot, or kill? minimum threshold to proceed?:** Time: a 6-week pilot. Week 1 sets the baseline and weeks 2–6 run the new flow, which leaves half of the 12-week roadmap to scale before the largest account’s renewal conversations.

Data: at least 4 full weeks of post-launch data from at least 2 pilot accounts, covering both Android and iOS drivers and weak-signal routes. Drivers run dozens of stops a day, so even about 30 drivers at around 40 stops over 20 working days gives roughly 24,000 confirmed stops. That’s more than enough to read the metric reliably.

What a pivot would look like: keep the one-tap flow and target the specific blocker. For example, add an offline upload queue if POD failures continue, or go back to the coordinator side if drivers confirm in the app but compliance time doesn’t fall.
- **Draft your full hypothesis sentence , one to three sentences; quote the metric, name the persona, name the outcome:** Based on drivers telling us that confirming a delivery takes “three screens, in the rain, at a doorstep” (UXR-01), and on Compliance being the weakest widely used frontline feature (Driver CSAT 2.8 at 64% adoption, with 14.6 min of coordinator compliance logging against a 3-min benchmark), I believe that making delivery confirmation and proof of delivery a reliable one-tap step for frontline delivery drivers will move compliance back inside RouteLogic, cutting daily workaround time and reversing the coordinator NPS collapse (+18 to −12) behind complexity-driven churn. This will be measured by the doorstep in-app confirmation rate rising from an estimated 65% or less to 90% or more (a gain of at least 25 points), alongside coordinator compliance time falling from 14.6 to 5 min or less. I will protect Manager Compliance CSAT at 3.9 or higher and make a go/no-go decision after a 6-week pilot (1 week of baseline, 5 weeks live, at least 2 accounts).
