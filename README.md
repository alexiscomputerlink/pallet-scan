# Pallet Scan Validation

Standalone app, independent of the Delivery Map. **This repo contains code only — no inventory data.**
After Microsoft sign-in (Entra app "Pallet Scan Validation", single tenant) the app reads devices from the SharePoint list
`PalletDevices` and writes every scan to `PalletScanLog` (site EntregasEscuelas).

- `index.html` – the whole app
- `routes.json` – route → color code (**currently placeholders**)

## Modes
**Clasificar por ruta:** scan a device → route color, route, school, region, pallet.
**Paletizar:** scan `PALLET-12`, then each device. Results: Green OK · Yellow other pallet same route+school · Orange other school same route · Red other route (rejected) · Purple not in inventory · Slate already scanned · Blue pallet complete. Yellow/orange can be reassigned by a supervisor (logged as REASIGNADO).

The SharePoint log is the source of truth: station state is rebuilt from it at startup and refreshed every 30 s. Scans made offline queue locally and sync when back online.
