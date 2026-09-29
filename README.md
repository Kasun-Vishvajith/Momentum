# Momentum frontend prototype

A complete, locally runnable HTML, CSS, and JavaScript design prototype. No backend, database, API key, build step, npm install, or external asset service is required.

## Start

1. Extract this ZIP completely.
2. Open `index.html` in a modern browser.
3. Choose a demo role on the sign-in screen, then press Sign in.

If your browser restricts local-file storage, use VS Code Live Server, or run `python -m http.server 8000` in this folder and open `http://localhost:8000`. This only serves static files. It is not an application backend.

## Demo credentials

| Persona | Username | Password |
| --- | --- | --- |
| K. Mendis, store manager | store | demo123 |
| D. Senanayake, dispatcher | dispatch | demo123 |
| R. Fernando, loader | loader | demo123 |
| S. Bandara, driver | driver | demo123 |
| A. Perera, optional administrator | admin | demo123 |

This is intentionally not secure authentication. Accounts and credentials are readable sample data stored in your browser. Never enter real passwords, personal information, or sensitive photos.

The four operating roles are the competition scope. The small administrator extension is included at the user's request; it manages local demo users and inspects the reference directory. It does not distract from the four-role delivery story.

## Connected judge walkthrough

Use Demo controls in the header to switch roles without losing shared progress. On mobile, it remains in the header. You can also sign out and sign in with the next account. All roles share data in the same browser and origin.

1. Start as **store**. Open My orders. Inspect the Chilled replenishment request. Expand references to see the source outlet and receiving window. Optionally create the one additional sample request; it becomes visible in the dispatcher queue. Repeated submission does not create duplicates.
2. Switch to **dispatcher**, open Planning. Assign Fresh Colombo 02 to the morning run. Fresh Colombo 01 and 03 are already on this draft. Total load is 90 crates, 720 kg, 5.6 m³.
3. Try assigning Style Colombo. Its volume does not fit. It was deferred previously, so the design explicitly exposes its service priority. Record a deferral with a reason and note, or leave it visible for another run.
4. Optionally select an ambient van or a truck and validate. Handling or van-only access blocks publication. A Kandy vehicle also fails the home-depot check. Restore VEH035, validate, then publish.
5. Switch to **loader**. The published plan appears. Loading order is the reverse of delivery order. Fresh Colombo 03 has 15 of 20 crates. Report the shortage, add the five replenished crates, verify all three consignments, then confirm loading.
6. Switch to **driver**. Start the run and mark arrival at the first stop. Record delivery. Use sample signature and photo for the demo, then save.
7. At Fresh Colombo 02, mark arrival, record the 40 crates, recipient, signature, and photo. Save draft if you want to explore another screen. Use Demo controls to simulate offline while preserving the saved draft. Save delivery. The sync page shows the record safely pending on this browser.
8. Simulate reconnect. Optionally use Demo controls to fail the next sync attempt. Retry after the failure. The same pending record is reconciled once, without adding another delivery.
9. Switch to **store**. Open the Chilled replenishment order and Review receipt. Driver quantities and evidence are visible. Confirm the actual received count. A difference requires a note and produces a dispatcher issue.
10. Switch to **dispatcher**, Trips, to review the issue and record its resolution. Visit Capacity for a restrained, clearly illustrative future demand outlook.
11. Switch to **driver**, finish the third stop, then confirm depot return. Driver recording, sync, and store receipt are distinct states.
12. Optional: sign in as **admin** to add, search, edit, deactivate, and delete demo users. Duplicate usernames are rejected. You cannot delete or disable your own active admin account.

## Checkpoint shortcuts

Demo controls has five presets: planning, loading shortage, driver ready, store receipt ready, and offline delivery saved. Applying a preset replaces operational progress after confirmation and preserves user accounts. Reset everything restores the original fixture and accounts.

For the after-cutoff recovery, open Demo controls, enable After-cutoff order scenario, and open Create order. The original date is retained, the revised request moves to 1 Oct, and explicit acknowledgement is required. Inputs remain preserved when switching this setting while editing.

## Deliberate scope

- Plain HTML, CSS, JavaScript with hash navigation. Browser Back works.
- Four operational experiences and a small user-admin extension.
- Fixed, coherent morning-run fixture. The order form supports one additional sample request (WP-1058), not unrestricted operational CRUD or a planning engine.
- Interactive allocation, compatibility checks, deferral reasons, loading gates, handover evidence, offline queue, receipt, issue handling, and user CRUD.
- Local persistence through localStorage, with an in-memory fallback message when unavailable. Session role uses sessionStorage.
- Simulated connectivity and synchronisation, not real network requests or background uploads. Under local-file mode, all app files are already on the device. When served over HTTP, reload availability depends on the server; this is not a service-worker PWA.
- Sample signature is marked as a prototype sample. The dock image is an original illustration, not a real proof-of-delivery photograph. Users may attach a local image for interface review.
- No map because the source outlet data contains no precise locations. Clear stop sequence and receiving constraints are the central decision aid.
- No real phone number, location tracking, temperature telemetry, trained forecasts, messaging, or production authentication.

## Responsive design

Desktop: stable left navigation, broad content area, compact operational cards, contextual secondary panel.
Tablet and phone (800px and below): one-column flow, large controls, floating bottom navigation with safe-area spacing. Important statuses remain textual. Tested targets include 1440, 1280, 768, 390, and 360 CSS pixels.

## Files

- `index.html`: application entry
- `styles.css`: responsive design system and all component styling
- `app.js`: routes, renderers, seeded interactions, local persistence
- `data/seed.js`: offline-readable supplied reference data
- `data/*.csv`: original challenge reference tables used in the prototype
- `assets/mark.svg`: Momentum route mark used across the product shell
- `assets/route-art.svg`: original editorial route illustration
- `assets/dock-sample.svg`: labelled sample evidence illustration
- `docs/design-guide.html`: personas, flows, screen rationales, failure scenarios, style guide, assumptions, submission checklist, and video outline
- `docs/coverage.md`: brief-to-interface mapping and intentional boundaries
- `docs/QA.md`: verification notes
- `ASSETS.md`: asset and source attribution

## Important changes from the earlier Stitch mockups

Fresh deliveries are scheduled before 8 AM, as the booklet requires. The source outlet IDs are OUT001, OUT002, and OUT003; the chosen source vehicle is VEH035. Friendly display names such as Fresh Colombo 02 are derived labels, not invented real store addresses. The earlier Kelaniya, WP-R12, and late-morning examples are not reused.

VEH035 supports 1,040 kg and 7.0 m³ and belongs to Peliyagoda. The illustrative three-stop run uses 32 km, 16-minute street service allowances, travel buffers, and a sample remaining weekly fuel balance of 120 L. That remaining balance is a demo assumption, not supplied telemetry.

## Designathon hand-in

The included design guide supports the written design deliverables. This ZIP is a reviewable frontend source package, not a claim that the entire competition submission is complete. You still need your team identity, a shareable prototype URL, the unlisted 3 to 5 minute video, and a final disclosure accurately reflecting your team's work. The booklet asks for one design file with distinct pages. Use the included guide and prototype as material for that submission format, or confirm acceptance of your HTML-based design file with the organisers.
