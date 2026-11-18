# Competitive Analysis & Journey Map (Module 2)

## Responses
- **Role, who are you solving for? (the specific user segment or profile):** The frontliner driver:
Role: A delivery driver who runs dozens of stops a day, often one-handed, outdoors and against the clock, on routes where the signal can’t be counted on (UXR-01, UXR-06, UXR-11).
- **Goal, what is this user ultimately trying to achieve?:** Goal: To get through each stop quickly and trust that the app will hold their route and record their work from the first stop to the last.
- **Friction, the main barrier (moment of misery) stopping them from succeeding:** Friction: The driver deals with two failures at once.
Too heavy: Marking a stop delivered takes “three screens, in the rain, at a doorstep, with a package in one hand” (UXR-01, BUG-2055). “Start Route,” which they tap about 30 times a day, is “buried under features I’ve never touched” (UXR-11, BUG-2079).
Too unreliable: Partway through a route, the app crashes and “lost my remaining stops.” Elena had to call the office to have them read out, and “twenty minutes gone” (UXR-03, BUG-2031). Without signal, the stop list doesn’t load at all, so Priti screenshots her route every morning as a backup (UXR-06, BUG-2050). About 35% of proof-of-delivery photos fail on weak signal without any error shown, so drivers take them “three times” (UXR-07, BUG-2061). On top of this, a reassigned route can take up to 15 minutes to reach them, so they end up driving on old instructions (UXR-02, BUG-2044).
- **External tools, the outside platforms or tools the user is forced to use:** SMS / text messaging: to report deliveries to the dispatcher instead of marking them in the app (UXR-01).
Phone calls to the office: to rebuild a lost route after a crash (UXR-03), and to get route changes faster than the app delivers them (UXR-02).
Phone screenshots: to save the stop list every morning in case they lose signal (UXR-06).
Paper manifest: a printed backup of the route, carried by 5 of 7 drivers (UXR-12).
WhatsApp group: where dispatch posts live route changes (UXR-02). We have evidence that dispatchers use it. That drivers rely on it is our inference.
- **The process, the 3 to 5 manual steps the user takes to get the job done:** 1. Before the shift: build a backup route

Screenshot the full stop list while there’s still signal (UXR-06).
Carry a paper manifest “just in case the app dies” (5 of 7 drivers, UXR-12).

Why it’s inefficient: Drivers do this prep every day for a failure that may not happen. Both copies are frozen when they’re made, so they go out of date as soon as dispatch changes the route. The backup only helps until the first reassignment.

2. At each stop: skip the app to report delivery

Instead of tapping through three screens to mark a stop delivered, text the dispatcher (UXR-01).
Mark the stop in the app later, or not at all. (Inferred: the research doesn’t say whether drivers go back and enter it in the app.)

Why it’s inefficient: It saves the driver a few seconds and moves the work to the dispatcher, who now has to read texts and reconcile them with the board by hand. The delivery is recorded in a chat thread, not in the system of record.

3. At proof of delivery: take the photo again and again

Take the photo, get no confirmation it uploaded, and take it again, sometimes three times (UXR-07, BUG-2061).

Why it’s inefficient: Each retake costs time at the doorstep and adds upload traffic on a weak connection that’s already failing. The driver still leaves without knowing whether any of the photos arrived.

4. When the app crashes: rebuild the route by phone

Call the office and have someone read out the remaining stops from their screen (UXR-03, BUG-2031).
Or fall back to the morning screenshot or paper manifest.

Why it’s inefficient: About 20 minutes are lost per incident, and two people are tied up: the driver and someone in the office. If the route changed since the morning, the paper or screenshot is already wrong.

5. When the route changes: take instructions from outside the app

Get the new route from the dispatcher by phone call or through the team WhatsApp group, because the change in the app arrives 8–15 minutes late (UXR-02, BUG-2044). (The dispatcher’s use of WhatsApp is documented. That drivers act on those messages is inferred, since the group only works if they do.)

Why it’s inefficient: Instructions now come from two places that can contradict each other. Drivers learn that the app is the slower and less trustworthy one, which makes them rely on it less in every other step.

6. Throughout the route: ignore the optimised route

Override the suggested route every day, using their own knowledge of road closures and loading docks (UXR-05, BUG-2068).

Why it’s inefficient: Drivers redo the same corrections daily because the app can’t save them. RouteLogic’s main promise, an optimised route, ends up working as a rough suggestion.
- **Core frustration, the exact moment the process feels most “broken”:** The moment the app crashes mid-route and the remaining stops disappear.

This is when the process feels most broken. The app fails at its most basic job, which is holding the route. The driver also can’t recover on their own: they have to stop working and call someone to read out their own route. The other frustrations slow the driver down. This one stops them completely. It is also the reason every other backup exists, because the screenshots and paper manifests are there for exactly this moment.
- **The evidence, a specific quote or behavior from the research that proves this:** The Evidence
Quote: “The app crashed mid-route and lost my remaining stops. I had to call the office to read them to me off a screen. Twenty minutes gone.” (Elena, driver, UXR-03)
Technical confirmation: BUG-2031 (Critical) records crashes on Android 12/13 once a route exceeds about 40 stops. The remaining route is lost and has to be reloaded from the server.
Behaviour: Five of seven drivers in the focus group carry a paper manifest “just in case the app dies” (UXR-12). That means drivers prepare for this failure every day, not only when it happens.
- **Your journey map, a shareable link, or the map file you committed (e.g. journey-map.html):** https://github.com/skjold94-beep/pm-final-project/blob/main/02-discovery/routelogic-velocity-driver-future-state.md
