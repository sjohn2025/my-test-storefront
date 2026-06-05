# Enriched Product Block

Displays a product card combining live catalog data (price, images) from Adobe Commerce via API Mesh with custom enrichment data (sustainability score, estimated delivery).

## Authored Structure

| Enriched Product |
|------------------|
| SKU              |

The block takes a single row with the product SKU as its value.

## Data Sources

- **Adobe Commerce Catalog** — product name, images, and pricing fetched via the `products` query
- **Enrichment API** — sustainability score, estimated delivery, and enrichment timestamp fetched via `Enrichment_getProductEnrichment`, both stitched together through the API Mesh GraphQL endpoint

## Sustainability Badge

The sustainability score from the enrichment API is rendered as a color-coded badge:

| Score    | Label     | Color  |
|----------|-----------|--------|
| 80–100   | Excellent | Green  |
| 60–79    | Good      | Yellow |
| 0–59     | Fair      | Red    |

## Pricing

Supports both `SimpleProductView` (single price) and `ComplexProductView` (price range — shows minimum final price).
