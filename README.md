# Quickstart for Bitasmbl project (.NET)

## 1) Install Bitasmbl-CLI package

```bash
npm i bitasmbl-cli
```

## 2) Run bitasmbl command to set up the project

```bash
bitasmbl pull --repoUrl  --appId 330 --repoId 0
```

## 3) Enter into the main directory and start coding!

```bash
cd 
```

## Customize requirements in a way you like

Bitasmbl organizes development into requirements. Each requirement describes a feature or implementation goal and can define suggested file locations through a `paths` array.

The `paths` property acts as a mapping guideline, helping contributors understand where related code should live.

You can customize `paths` mappings through the `bitasmbl.json` file.

```json
{
  "requirement": "Implement authentication flow",
  "paths": ["**/src/features/auth/**", "**/src/components/auth/**"]
}
```

## Requirements

### Product Discovery UI and Navigation

Build product listing, category filters, and navigation so users quickly find organic products.

Suggested paths:

```txt
**/src/components/product-list/**
**/src/components/filters/**
**/src/components/navigation/**
**/src/hooks/productDiscovery/**
```

### Product Detail and Reviews Experience

Implement product detail pages showing organic labels, nutrition info, and user reviews.

Suggested paths:

```txt
**/src/pages/product-detail/**
**/src/components/product-media/**
**/src/components/reviews/**
**/src/hooks/productDetail/**
```

### Shopping Cart and Checkout Flow UI

Provide cart management, shipping options, and checkout steps optimized for quick purchase.

Suggested paths:

```txt
**/src/pages/cart/**
**/src/pages/checkout/**
**/src/components/cart-summary/**
**/src/hooks/checkoutFlow/**
```

### Personalized Recommendations and Search UI

Create search, suggested items, and health-focused recommendations for easier discovery.

Suggested paths:

```txt
**/src/pages/search/**
**/src/components/search-bar/**
**/src/components/recommendations/**
**/src/hooks/searchExperience/**
```

### Accessibility and Mobile Responsiveness

Ensure responsive layout, keyboard navigation, and ARIA support for all key purchase flows.

Suggested paths:

```txt
**/src/styles/responsive/**
**/src/components/a11y/**
**/src/hooks/useResponsiveLayout/**
**/src/utils/a11y/**
```

### Product Catalog and Category API

Expose APIs for organic product catalog, categories, and dietary tags for filtering.

Suggested paths:

```txt
**/src/OrganicShop.Catalog.Api/Controllers/**
**/src/OrganicShop.Catalog.Api/Models/**
**/src/OrganicShop.Catalog.Core/Services/**
**/src/OrganicShop.Catalog.Infrastructure/Repositories/**
```

### Search and Recommendation Backend

Implement search endpoints and recommendation logic tailored to health-focused users.

Suggested paths:

```txt
**/src/OrganicShop.Search.Api/Controllers/**
**/src/OrganicShop.Search.Core/Services/**
**/src/OrganicShop.Search.Infrastructure/Indexing/**
**/src/OrganicShop.Search.Infrastructure/Queries/**
```

### Cart, Orders, and Checkout API

Provide secure endpoints for cart operations, order creation, and checkout validation.

Suggested paths:

```txt
**/src/OrganicShop.Orders.Api/Controllers/**
**/src/OrganicShop.Orders.Core/Services/**
**/src/OrganicShop.Orders.Infrastructure/Repositories/**
**/src/OrganicShop.Orders.Core/Workflows/**
```

### Payments and Transaction Security

Integrate payment providers and enforce secure transaction handling and auditing.

Suggested paths:

```txt
**/src/OrganicShop.Payments.Api/Controllers/**
**/src/OrganicShop.Payments.Core/Services/**
**/src/OrganicShop.Payments.Infrastructure/Gateways/**
**/src/OrganicShop.Security/Policies/**
```

### User Profiles and Preferences

Support user accounts, delivery addresses, and dietary preferences for tailored shopping.

Suggested paths:

```txt
**/src/OrganicShop.Users.Api/Controllers/**
**/src/OrganicShop.Users.Core/Services/**
**/src/OrganicShop.Users.Infrastructure/Repositories/**
**/src/OrganicShop.Users.Core/Preferences/**
```



## Requirement Evaluation

Bitasmbl includes a requirement evaluation workflow that lets contributors select a task and submit work for validation.

Run:

```bash
bitasmbl evaluate
```

Example output:

<pre>
? Available Requirements:

❯ [<span style="color:#9333ea">1</span>] <span style="color:#9333ea"> Define portfolio layout </span>            [3]
  [2] Build showcase components            [3]
  [3] Implement navigation routing         [3]
</pre>

`[x]` on the right represents the number of submission attempts remaining for a requirement.

## Example evaluation result

```csharp
/*
|--------------------------------------------------------------------------
| BITASMBL EVALUATION
|--------------------------------------------------------------------------
| REQUIREMENT:
| Implement product catalog API
|
| SCORE: 12/100
| STATUS: FAIL ✕
|
| INSIGHT:
| The endpoint returns static product data and does not use a repository,
| service layer, filtering, or async database access.
|--------------------------------------------------------------------------
*/

using Microsoft.AspNetCore.Mvc;

namespace BitasmblProject.Features.Catalog;

[ApiController]
[Route("api/products")]
public sealed class ProductsController : ControllerBase
{
    [HttpGet]
    public IActionResult GetProducts()
    {
        var products = new[]
        {
            new { Id = 1, Name = "Keyboard", Price = 89.99 },
            new { Id = 2, Name = "Mouse", Price = 49.99 }
        };

        return Ok(products);
    }
}
```

## Learn More

For complete command references, workflow explanations, and additional documentation, visit:

👉 [Bitasmbl Documentation](https://bitasmbl.com/docs)