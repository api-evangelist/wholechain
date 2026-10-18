---
name: wholechain-record-traceability-events
description: Push supply chain traceability events (commission, aggregation, ship, receive, transform, observe) from an ERP into Wholechain, synchronously or via the async queue, and remove a wrong event.
api: wholechain:wholechain-connect-api
generated: '2026-10-18'
method: generated
source: openapi/wholechain-openapi.yml
operations:
- ProcessEvents
- EnqueueEvents
- GetJobs
- DeleteEvent
---
# Record traceability events

Base URL: `https://connect.wholechain.com` (sandbox: `https://connect-sandbox.wholechain.com`). Send the `X-API-KEY` header on every call ([Authentication](https://developers.wholechain.com/GettingStarted/Authentication/)).

1. Make sure the products and locations the events reference already exist (see `wholechain-manage-master-data`).
2. For a small batch, `POST /Integration/Events` (**ProcessEvents**). The body can be JSON, XML or CSV. Event shapes and bizsteps are described at https://developers.wholechain.com/EventsV2/Introduction/.
3. For large batches, `POST /Integration/Events/async` (**EnqueueEvents**), then check progress with `GET /Integration/Jobs` (**GetJobs**).
4. To remove a wrong event, `DELETE /Integration/Events/{eventId}` (**DeleteEvent**). See https://developers.wholechain.com/EventsV2/Removing_events/.

Notes: the spec declares no idempotency key, so retrying a POST can create duplicate events. Check before you resubmit. Status codes are listed at https://developers.wholechain.com/GettingStarted/HTTP_status_codes/.
