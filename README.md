# Momentum · Waypoint

Waypoint is a static frontend prototype for delivery operations. It connects the full handoff journey in one workspace:

**Request → Plan → Load → Deliver → Sync → Receive → Resolve**

The prototype is built with plain HTML, CSS, and JavaScript. It does not require a backend, database, API key, package installation, build step, or external asset service.

## Run locally

### Option 1: Open the page directly

Open [`index.html`](index.html) in a modern browser, choose a demo role, and select **Sign in**.

### Option 2: Serve the folder locally

Serving the folder over HTTP gives the browser a consistent origin for local storage and is recommended for a complete walkthrough:

```bash
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000).

This is a static file server only; it is not an application backend.

## Demo accounts

All accounts use the password `demo123`.

| Role | Username | Use it to explore |
| --- | --- | --- |
| Store manager | `store` | Submit orders and confirm received quantities |
| Dispatcher | `dispatch` | Allocate capacity, validate, publish, and resolve issues |
| Loader | `loader` | Reconcile shortages and confirm the loading manifest |
| Driver | `driver` | Run stops, record handovers, and test offline sync |
| Administrator | `admin` | Manage sample users and inspect the operating directory |

These are intentionally local demo credentials, not secure authentication. Do not enter real passwords, personal information, or sensitive photos.

## Suggested walkthrough

1. Sign in as `store` and open **My orders**. Inspect the chilled replenishment request and its receiving window.
2. Switch to `dispatch` with **Demo controls**, open **Planning**, assign the Fresh Colombo morning orders, validate the vehicle, and publish the run.
3. Switch to `loader`. Follow the reverse delivery order, report the five-crate shortage, replenish it, verify the manifest, and confirm loading.
4. Switch to `driver`. Start the run, arrive at a stop, and record a handover using the sample signature and photo.
5. Use **Demo controls** to test an offline delivery, reconnect, retry a failed sync, and confirm that the record is reconciled once.
6. Switch back to `store` and confirm the actual received quantity. A discrepancy creates a reviewable dispatcher issue.
7. Use `admin` to explore the optional local user-management extension.

The **Demo controls** menu also provides shortcuts for planning, loading shortage, driver-ready, store-receipt-ready, and offline-delivery scenarios. Resetting the demo restores the original fixture and accounts.

## What the prototype demonstrates

- Role-specific workspaces for store, dispatcher, loader, driver, and administrator users.
- Order requests, allocation, capacity checks, handling constraints, deferrals, and publication.
- Loading sequence, shortage reporting, replenishment, and verification gates.
- Delivery quantities, recipient details, signature/photo evidence, drafts, and offline queueing.
- Sync retry and duplicate-safe reconciliation states.
- Separate driver handover and store receipt confirmation checkpoints.
- Receipt discrepancies and dispatcher issue resolution.
- Responsive desktop, tablet, and phone layouts with keyboard-focusable controls.
- Local persistence through `localStorage`, with an in-memory fallback when browser storage is unavailable.

## Intentional scope

This is a reviewable interaction and visual prototype, not a production logistics system. It intentionally does not provide live maps, GPS, telemetry, messaging, real authentication, a planning engine, live network synchronization, or unrestricted operational CRUD.

The fixture uses a coherent Colombo morning run. Vehicle capacity, travel time, fuel balance, route timing, and evidence images are clearly presented as prototype assumptions or sample assets.

## Project structure

```text
.
├── index.html                 # Application entry point
├── styles.css                 # Responsive design system and components
├── app.js                     # Routes, views, interactions, and local state
├── data/
│   └── seed.js                # Offline-readable demo fixture
├── assets/
│   ├── mark.svg               # Product mark
│   ├── route-art.svg          # Login illustration
│   └── dock-sample.svg        # Sample delivery evidence illustration
└── docs/
    ├── design-guide.html      # Personas, flows, rationale, and assumptions
    └── previews/              # Design-guide preview images
```

## Design guide

Open [`docs/design-guide.html`](docs/design-guide.html) for the personas, connected flows, screen rationale, recovery scenarios, design system, assumptions, and submission checklist.

## Browser support

Use a current version of Chrome, Edge, Firefox, or Safari. The interface is designed for desktop widths and for phone widths of approximately 390–360 CSS pixels. Browser storage is scoped to the current browser origin.

## License and usage

This repository contains a designathon prototype and sample data. Review the source and asset attribution before reusing any part of it in another project.
