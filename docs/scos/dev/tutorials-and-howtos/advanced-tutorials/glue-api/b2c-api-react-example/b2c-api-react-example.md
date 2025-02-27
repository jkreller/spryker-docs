---
title: B2C API React example
description: B2C API React Example is a single-page web application that demonstrates the use of Spryker Glue REST API in B2C scenarios.
last_updated: Jun 16, 2021
template: howto-guide-template
originalLink: https://documentation.spryker.com/2021080/docs/b2c-api-react-example
originalArticleId: 094f9906-b82e-49aa-9af5-27199c5d2c01
redirect_from:
  - /2021080/docs/b2c-api-react-example
  - /2021080/docs/en/b2c-api-react-example
  - /docs/b2c-api-react-example
  - /docs/en/b2c-api-react-example
  - /v6/docs/b2c-api-react-example
  - /v6/docs/en/b2c-api-react-example
  - /v5/docs/b2c-api-react-example
  - /v5/docs/en/b2c-api-react-example
  - /v4/docs/b2c-api-react-example
  - /v4/docs/en/b2c-api-react-example
  - /v3/docs/b2c-api-react-example
  - /v3/docs/en/b2c-api-react-example
  - /v2/docs/b2c-api-react-example
  - /v2/docs/en/b2c-api-react-example
  - /v1/docs/b2c-api-react-example
  - /v1/docs/en/b2c-api-react-example
related:
  - title: B2C API React example installation
    link: docs/scos/dev/tutorials-and-howtos/advanced-tutorials/glue-api/b2c-api-react-example/b2c-api-react-example-installation.html
  - title: Glue REST API
    link: docs/scos/dev/glue-api-guides/page.version/glue-rest-api.html
  - title: REST API Reference
    link: docs/scos/dev/glue-api-guides/page.version/rest-api-reference.html
---

As a part of documentation related to Spryker Glue REST API, we have also developed a B2C API React Example. It is a [React](https://reactjs.org/) single page application based on a [webpack](https://webpack.js.org/) devserver, Typescript, [Redux](https://redux.js.org/), and Material UI.

The application has been developed for four primary purposes:

1. Provide a simple yet fully functional example of Glue REST API usage.
2. Illustrate a complete B2C Spryker experience using REST endpoints, starting from selecting the necessary product all the way through to placing an order. The shop also demonstrates the use of the API resources to create such features as the product catalog, search, auto-suggestions, customer registration, cart management, displaying order details.
3. Allow you to try Glue REST API without any coding.
4. Provide sample REST requests that can facilitate custom touchpoint development.

{% info_block errorBox %}

The shop is provided only for display purposes, and must under no circumstances be used as a starting point for any project.

{% endinfo_block %}

## API resources

The Demo shop was built using and demonstrates the use of the endpoints and resources provided by the following APIs:


| API | REFERENCE DOCUMENTS |
| --- | --- |
| Search API | [Catalog search](/docs/scos/dev/glue-api-guides/{{site.version}}/searching-the-product-catalog.html)<br>[Getting suggestions for auto-completion and search](/docs/scos/dev/glue-api-guides/{{site.version}}/retrieving-autocomplete-and-search-suggestions.html) |
| Category API | [Retrieving category trees](/docs/scos/dev/glue-api-guides/{{site.version}}/retrieving-categories/retrieving-category-trees.html) |
| Product API | [Retrieving abstract products](/docs/scos/dev/glue-api-guides/{{site.version}}/managing-products/abstract-products/retrieving-abstract-products.html)<br>[Retrieving concrete products](/docs/scos/dev/glue-api-guides/{{site.version}}/managing-products/concrete-products/retrieving-concrete-products.html) |
| Product Availability API | [Retrieve abstract product availability](/docs/pbc/all/warehouse-management-system/manage-using-glue-api/retrieve-abstract-product-availability.html)<br>[Retrieve concrete product availability](/docs/scos/dev/glue-api-guides/{{site.version}}/managing-products/concrete-products/retrieving-concrete-product-availability.html) |
| Product Price API | [Retrieving abstract product prices](/docs/pbc/all/price-management/manage-using-glue-api/retrieve-abstract-product-prices.html)<br>[Retrieving concrete product prices](/docs/pbc/all/price-management/manage-using-glue-api/retrieve-concrete-product-prices.html) |
| Product Tax Sets API | [Retrieving product tax sets](/docs/pbc/all/tax-management/manage-via-glue-api/retrieve-tax-sets.html) |
| Product Image Sets API | [Retrieving image sets of abstract products](/docs/scos/dev/glue-api-guides/{{site.version}}/managing-products/abstract-products/retrieving-image-sets-of-abstract-products.html)<br>[Retrieving image sets of concrete products](/docs/scos/dev/glue-api-guides/{{site.version}}/managing-products/concrete-products/retrieving-image-sets-of-concrete-products.html) |
| Product Labels API | [Retrieving product labels](/docs/scos/dev/glue-api-guides/{{site.version}}/managing-products/retrieving-product-labels.html) |
| Login API | [Authentication and authorization](/docs/scos/dev/glue-api-guides/{{site.version}}/authentication-and-authorization.html) |
| Customer API | [Managing customers](/docs/scos/dev/glue-api-guides/{{site.version}}/managing-customers/managing-customers.html) |
| Cart API | [Guest carts](/docs/pbc/all/cart-and-checkout/manage-using-glue-api/manage-guest-carts/manage-guest-carts.html)<br>[Carts of registered users](/docs/pbc/all/cart-and-checkout/manage-using-glue-api/manage-carts-of-registered-users/manage-items-in-carts-of-registered-users.html) |
| Checkout API | [Checking out purchases and getting checkout data](/docs/pbc/all/cart-and-checkout/manage-using-glue-api/check-out/check-out-purchases.html) |
| Order History API | [Retrieving customer's order history](/docs/scos/dev/glue-api-guides/{{site.version}}/retrieving-orders.html) |
| Wishlist API | [Managing wishlists](/docs/pbc/all/shopping-list-and-wishlist/manage-via-glue-api/manage-wishlists-via-glue-api.html) |
| Store API | [Retrieving store configuration](/docs/scos/dev/glue-api-guides/{{site.version}}/retrieving-store-configuration.html) |

## Running the example application

The app source code can be found in the following GitHub repository: [https://github.com/spryker-shop/b2c-api-react-example](https://github.com/spryker-shop/b2c-api-react-example). You can install it inside [Spryker Development Virtual Machine](/docs/scos/dev/sdk/development-virtual-machine-docker-containers-and-console.html) or on a dedicated web server.

For detailed installation steps, see [B2C API React Example Installation](/docs/scos/dev/tutorials-and-howtos/advanced-tutorials/glue-api/b2c-api-react-example/b2c-api-react-example.html).

## Peeking requests

After installing and running the example app, you can try its functionality. Depending on how you installed it, the shop is available at:

* `http://glue.de.b2c-demo-shop.local/react/`—when installed it in the VM;
* `http://react.local`—when installed on a separate web server.

To get a list of Glue API requests that have been used to build a page, follow these steps:

1. Open the F12 menu of your web browser.
2. Activate the **Console** section.
3. To get details of a specific request, expand it in the console.

![glue-requests-sample.png](https://spryker.s3.eu-central-1.amazonaws.com/docs/Glue+API/B2C+API+React+Example/glue-requests-sample.png)
