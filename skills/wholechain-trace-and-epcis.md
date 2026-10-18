---
name: wholechain-trace-and-epcis
description: Trace a lot/serial or purchase order through the supply chain, check inventory, and exchange EPCIS data (capture documents and poll their status).
api: wholechain:wholechain-connect-api
generated: '2026-10-18'
method: generated
source: openapi/wholechain-openapi.yml
operations:
- ListEventDetails
- GetInventory
- Capture
- GetCaptureStatus
- ListCaptureStatus
---
# Trace and exchange EPCIS data

Send the `X-API-KEY` header on every call.

1. Trace: `GET /epcis/Events/details` (**ListEventDetails**) with `LotSerial` or `PurchaseOrder`. Set `PerformTraceback` to walk upstream, and page with `PageNumber`/`PageSize`.
2. Inventory: `GET /Integration/Inventory` (**GetInventory**), filtered by `ProductIds`, `LocationIds` and `AfterDate`.
3. EPCIS ingest: `POST /epcis/Capture` (**Capture**) with an EPCIS document. Then poll `GET /epcis/Capture/{captureId}` (**GetCaptureStatus**), or list captures with `GET /epcis/Capture` (**ListCaptureStatus**). See https://developers.wholechain.com/EventsV2/receiving_Epcis/.
