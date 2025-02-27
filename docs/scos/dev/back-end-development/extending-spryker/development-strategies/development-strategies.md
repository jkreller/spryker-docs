---
title: Development strategies
description: This instruction describes the strategies a project team can take while building a Spryker-based project.
last_updated: Jan 28, 2022
template: concept-topic-template
---

Spryker OS exposes codebase projects, which enables a high level of customization and can satisfy even the most complex project business requirements.

In the project development, the team is free to decide what approach to use. Spryker recommends considering *Configuration*, *Plug and Play*, and *Project modules* first to get maximum from the Spryker OS codebase, atomic releases, leverage minimum efforts for the integration of the new features, and keep the system up to date.

Before proceeding to the strategies definition, check out the following table of the Spryker OS update support to make the best decision about the customization strategy.

| DEVELOPMENT STRATEGY | SPRYKER OS UPDATE SUPPORT |
| --- | --- |
| Configuration | High, you can safely take minor and patch releases. |
| Plug and play | High, you can safely take minor and patch releases. |
| Project modules | High, you can safely take minor and patch releases. |
| Spryker OS module customization | Reduced, manual check is needed for every update. |
| Spryker OS module replacement | No support. |

## Development strategies

Consider the following development strategies.

### Configuration

Spryker provides an extensive configuration capability using `DependencyProviders` and Configuration.

Existing Spryker modules remain untouched.

{% info_block infoBox "Example" %}

To adjust Spryker behavior to the project needs, you can extend `\Spryker\Zed\Product\ProductConfig` on the project and adjust the number of products shown in the suggestion `\Pyz\Zed\Product\ProductConfig::getFilteredProductsLimitDefault()` to `20`.

{% endinfo_block %}

{% info_block infoBox "Example" %}

In your project, you don't calculate a refundable amount inside Spryker OS, so you need to extend `\Spryker\Zed\Calculation\CalculationDependencyProvider` by
`\Pyz\Zed\Calculation\CalculationDependencyProvider` and remove `RefundableAmountCalculatorPlugin` from the `CalculationDependencyProvider::getQuoteCalculatorPluginStack()` plugin stack.

{% endinfo_block %}

Spryker OS support: High, you can safely take minor and patch releases.

### Plug and play

When existing OOTB functionality is not enough, we need to consider building our Plugins for existing plugin stacks in separate Project modules.

The existing Spryker modules remain untouched.

{% info_block infoBox "Example" %}

In your project, you don't store prices in Spryker OS, but in an external system. You need to create a new module `SuperPrice` with a new plugin `\Pyz\Zed\SuperPrice\Communication\Plugin\Calculator\PriceCalculatorPlugin`, which performs a call to my Super ERP and gathers prices. Once it's done, you replace default `\Spryker\Zed\Calculation\Communication\Plugin\Calculator\PriceCalculatorPlugin` with my Project `PriceCalculatorPlugin`.

{% endinfo_block %}

Spryker OS support: High, you can safely take minor and patch releases.

### Project modules

When the Spryker OS does not provide certain functionality, domain object, or concept, create a new Project module where you implement new business requirements.

The existing Spryker modules remain untouched.

{% info_block infoBox "Example" %}

In your project, you want to introduce product Label groups. In this case, you need to introduce a new project module `ProductLabelGroup`, which provides a new domain object `ProductLabelGroup` in a database (by adding `product_label_group.schema.xml` to the `Persistence` layer to Zed) and calls `ProductLabelFacade::findLabelById()` and `ProductLabelFacade::findAllLabels()` to manage the `ProductLabel` to `ProductLabelGroup` relations.

{% endinfo_block %}

Spryker OS support: High, you can safely take minor and patch releases.

### Spryker OS module customization

When specific OOTB Spryker behavior doesn't fit Project requirements, you can enable the full power of available for your codebase by extending existing business modules.

{% info_block infoBox "Let us know which extension point is missing, so we can add it in the core" %}

Register missing extension points in [Aha ideas](https://spryker.ideas.aha.io/).
 
{% endinfo_block %}

As it's quite a substantial change, we need to go deeper and not only extend OOTB Spryker behaviors but also change them, some of the non-API changes become dangerous. That's why a module constraint to a specific minor version is required (using *~* instead of *^*).

Consider using the composition design pattern instead of the direct class extensions: it could increase development costs, but also increases vendor support and simplifies minor updates.

{% info_block infoBox "Example" %}

In your project, the `Order` entity must not be hydrated during the buying process (you are building a vitrine). In this case, you need to create `\Pyz\Zed\Sales\Business\Order\OrderReader`, which extends the existing `\Spryker\Zed\Sales\Business\Order\OrderReader` and replace the implementation of `findOrderByIdSalesOrdermethod()`, where you adjust the hydration calls.

{% endinfo_block %}

Spryker OS support: Reduced, manual check is needed for every update.

### Spryker OS module replacement

When an existing Spryker module provides functionality that doesn't fit the Project conceptually, there is a possibility to replace a Spryker module completely using the "composer replace" feature.

This option is not available for every module, as sometimes conceptual changes could lead to high development efforts.

{% info_block infoBox "Example" %}

In your project, the URL must be built in a completely different concept that Spryker offers. In this case, you need to create a project module URL, provide an implementation for every API function (Facade, Client, or Service) and replace OOTB module `spryker/url` with `my-super-project/url`. Spryker features based on URL use the project implementation to process URLs.

{% endinfo_block %}

Spryker OS support: No support.
