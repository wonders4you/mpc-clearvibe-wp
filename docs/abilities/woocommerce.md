# WooCommerce Abilities (113)

The For-WooCommerce add-on adds 113 abilities across 2 categories. All abilities are prefixed with `mpc-clearvibe-wp/for-woo-`. Both categories are **disabled by default**.

## Categories

| Category | Count | Default | Description |
|----------|-------|---------|-------------|
| `for-woo` | 103 | **Disabled** | Products, orders, coupons, shipping, tax, reports, settings, variations, attributes, reviews, notes, downloads, emails |
| `for-woo-customers` | 10 | **Disabled** | Customer data (personal data — GDPR warning) |

## for-woo (103 abilities — disabled by default)

### Products

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-products` | List products (filter by SKU via search) | Read |
| `for-woo-get-product` | Get a product by ID | Read |
| `for-woo-create-product` | Create a simple product | Write |
| `for-woo-update-product` | Update a product | Write |
| `for-woo-delete-product` | Delete a product (force skips trash) | Write |
| `for-woo-update-stock` | Update stock quantity | Write |
| `for-woo-bulk-update-price` | Bulk update product prices | Write |
| `for-woo-bulk-update-status` | Bulk update product status | Write |
| `for-woo-bulk-update-stock` | Bulk update stock quantity | Write |
| `for-woo-set-gallery` | Set product image gallery | Write |
| `for-woo-set-cross-sells` | Set cross-sell products | Write |
| `for-woo-set-up-sells` | Set up-sell products | Write |
| `for-woo-set-related` | Set related products | Write |

### Variations

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-variations` | List variations for a variable product | Read |
| `for-woo-get-variation` | Get a variation with attributes | Read |
| `for-woo-create-variation` | Create a variation | Write |
| `for-woo-update-variation` | Update a variation | Write |
| `for-woo-delete-variation` | Delete a variation | Write |

### Attributes

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-attributes` | List product attributes | Read |
| `for-woo-create-attribute` | Create a product attribute | Write |
| `for-woo-update-attribute` | Update a product attribute | Write |
| `for-woo-delete-attribute` | Delete a product attribute | Write |
| `for-woo-list-attribute-terms` | List terms for an attribute | Read |
| `for-woo-create-attribute-term` | Create an attribute term | Write |
| `for-woo-delete-attribute-term` | Delete an attribute term | Write |

### Product Categories & Tags

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-product-categories` | List product categories | Read |
| `for-woo-create-product-category` | Create a product category | Write |
| `for-woo-delete-product-category` | Delete a product category | Write |
| `for-woo-list-product-tags` | List product tags | Read |
| `for-woo-create-product-tag` | Create a product tag | Write |
| `for-woo-update-product-tag` | Update a product tag | Write |
| `for-woo-delete-product-tag` | Delete a product tag | Write |

### Orders

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-orders` | List orders | Read |
| `for-woo-get-order` | Get an order with line items | Read |
| `for-woo-update-order-status` | Update order status | Write |
| `for-woo-trash-order` | Move an order to trash | Write |
| `for-woo-restore-order` | Restore an order from trash | Write |
| `for-woo-delete-order` | Permanently delete an order | Write |
| `for-woo-list-order-items` | List line items in an order | Read |
| `for-woo-add-order-item` | Add a product to an order | Write |
| `for-woo-remove-order-item` | Remove a line item from an order | Write |

### Refunds

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-refunds` | List refunds for an order | Read |
| `for-woo-create-refund` | Create a refund | Write |

### Order Notes & Meta

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-order-notes` | List notes for an order | Read |
| `for-woo-create-order-note` | Add a note to an order | Write |
| `for-woo-delete-order-note` | Delete an order note | Write |
| `for-woo-get-order-meta` | Get order meta by key | Read |
| `for-woo-update-order-meta` | Add or update order meta | Write |
| `for-woo-delete-order-meta` | Delete order meta by key | Write |
| `for-woo-get-product-meta` | Get product meta by key | Read |
| `for-woo-update-product-meta` | Add or update product meta | Write |
| `for-woo-delete-product-meta` | Delete product meta by key | Write |

### Coupons

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-coupons` | List coupons | Read |
| `for-woo-get-coupon` | Get a coupon by ID | Read |
| `for-woo-create-coupon` | Create a coupon | Write |
| `for-woo-update-coupon` | Update a coupon | Write |
| `for-woo-delete-coupon` | Delete a coupon | Write |

### Shipping

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-shipping-methods` | List available shipping methods | Read |
| `for-woo-list-shipping-zones` | List shipping zones | Read |
| `for-woo-create-shipping-zone` | Create a shipping zone | Write |
| `for-woo-update-shipping-zone` | Update a shipping zone | Write |
| `for-woo-delete-shipping-zone` | Delete a shipping zone | Write |
| `for-woo-add-shipping-zone-method` | Add a shipping method to a zone | Write |
| `for-woo-add-zone-location` | Add a location to a shipping zone | Write |
| `for-woo-list-zone-locations` | List locations for a shipping zone | Read |
| `for-woo-list-shipping-classes` | List product shipping classes | Read |
| `for-woo-create-shipping-class` | Create a shipping class | Write |
| `for-woo-update-shipping-class` | Update a shipping class | Write |
| `for-woo-delete-shipping-class` | Delete a shipping class | Write |
| `for-woo-assign-shipping-class` | Assign a shipping class to a product | Write |

### Tax

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-tax-rates` | List tax rates | Read |
| `for-woo-create-tax-rate` | Create a tax rate | Write |
| `for-woo-update-tax-rate` | Update a tax rate | Write |
| `for-woo-delete-tax-rate` | Delete a tax rate | Write |
| `for-woo-list-tax-classes` | List tax classes | Read |
| `for-woo-create-tax-class` | Create a tax class | Write |
| `for-woo-delete-tax-class` | Delete a tax class | Write |

### Payment Gateways

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-payment-gateways` | List payment gateways | Read |
| `for-woo-update-payment-gateway` | Enable or disable a gateway | Write |
| `for-woo-get-gateway-settings` | Get gateway settings (sensitive redacted) | Read |
| `for-woo-update-gateway-settings` | Update gateway settings (sensitive blocked) | Write |

### Reviews

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-reviews` | List product reviews | Read |
| `for-woo-update-review-status` | Approve/hold/spam/trash a review | Write |
| `for-woo-delete-review` | Delete a product review | Write |

### Downloads

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-downloads` | List downloadable files for a product | Read |
| `for-woo-create-download` | Add a downloadable file | Write |
| `for-woo-update-download` | Update a downloadable file | Write |
| `for-woo-delete-download` | Remove a downloadable file | Write |

### Reports

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-sales-report` | Sales totals for a date range | Read |
| `for-woo-orders-report` | Order counts by status | Read |
| `for-woo-products-report` | Top-selling products by revenue | Read |
| `for-woo-customers-report` | New vs returning customers | Read |

### Settings

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-get-settings` | Get WooCommerce settings (sensitive redacted) | Read |
| `for-woo-update-settings` | Update settings (sensitive blocked) | Write |

### Emails

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-emails` | List transactional emails | Read |
| `for-woo-update-email-status` | Enable or disable an email | Write |
| `for-woo-resend-order-email` | Trigger a transactional email for an order | Write |

### Admin Notes

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-notes` | List WooCommerce admin notes | Read |
| `for-woo-create-note` | Create an admin note | Write |
| `for-woo-delete-note` | Delete an admin note | Write |

### Maintenance

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-system-status` | WooCommerce system status | Read |
| `for-woo-run-tool` | Run a maintenance tool | Write |
| `for-woo-clear-transients` | Clear WooCommerce transients | Write |
| `for-woo-clear-sessions` | Clear all WooCommerce sessions | Write |

## for-woo-customers (10 abilities — disabled by default)

> **GDPR Warning:** This category contains personal data (names, emails, addresses). Enable only if you accept the privacy risk.

| Ability | Description | R/W |
|---------|-------------|-----|
| `for-woo-list-customers` | List customers | Read |
| `for-woo-get-customer` | Get a customer with billing details | Read |
| `for-woo-create-customer` | Create a customer | Write |
| `for-woo-update-customer` | Update a customer | Write |
| `for-woo-delete-customer` | Delete a customer (reassigns orders) | Write |
| `for-woo-customer-orders` | List orders for a customer | Read |
| `for-woo-list-customer-downloads` | List download permissions | Read |
| `for-woo-update-billing-address` | Update customer billing address | Write |
| `for-woo-update-shipping-address` | Update customer shipping address | Write |
