---
name: wholechain-manage-master-data
description: Create, list and update the Wholechain products and locations/trade partners that traceability events reference.
api: wholechain:wholechain-connect-api
generated: '2026-10-18'
method: generated
source: openapi/wholechain-openapi.yml
operations:
- ProcessProducts
- GetPaginatedProducts
- UpdateProduct
- ProcessLocations
- ListLocations
- GetLocation
- UpdateLocation
---
# Manage products and locations

Send the `X-API-KEY` header on every call.

1. Search existing products with `GET /Integration/Products` (**GetPaginatedProducts**). Filter with `ExternalIdentifier`, `Urn` or `Upc`, and page with `PageNumber`/`PageSize`.
2. Create missing products with `POST /Integration/Products` (**ProcessProducts**), or update one with `PUT /Integration/Product` (**UpdateProduct**). See https://developers.wholechain.com/Products/Product_Creation/.
3. List locations and trade partners with `GET /Integration/Locations` (**ListLocations**), or fetch one with `GET /Integration/Location/{locationId}` (**GetLocation**).
4. Create them with `POST /Integration/Locations` (**ProcessLocations**), or update one with `PUT /Integration/Location` (**UpdateLocation**). See https://developers.wholechain.com/Locations/Creating_Loc_TP/.
