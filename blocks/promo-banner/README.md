# Promo Banner Block

Displays a grid of products from a specified category, fetched via Commerce Services GraphQL.

## Overview

The promo banner queries a product category and renders a responsive image grid with product names and prices. It is intended for promotional placement on landing and category pages.

## Configuration

Author the block with the following rows:

| Field | Description | Default |
|---|---|---|
| `category-id` | Commerce category ID to fetch products from | *(empty)* |
| `heading` | Section heading displayed above the grid | `Featured Products` |
| `max-products` | Maximum number of products to display | `4` |

## Behavior

1. On load the block immediately renders a "Loading products…" placeholder.
2. It fires a GraphQL `productSearch` query against the Commerce Services catalog filtered by `categoryIds`.
3. On success, products are rendered as linked cards with image, name, and price.
4. If the category returns no products, a "No products found." message is shown instead.

## Error Handling

If the GraphQL request fails for any reason (network error, missing config, etc.), the products container shows "Unable to load products." and the error is logged to the console via `console.error`.

## Integration

- Requires `CS_FETCH_GRAPHQL` and `getProductLink` from `scripts/commerce.js`.
- Product URLs are built using `getProductLink(urlKey, sku)` — ensure the commerce configuration is correct for the environment.
- Images are lazy-loaded and sized at 300×300 px.
