---
title: "HowTo: Replace Spryker module dependencies"
last_updated: Jun 16, 2021
template: howto-guide-template
originalLink: https://documentation.spryker.com/2021080/docs/ht-replace-bundle-dependencies
originalArticleId: d8499e40-0c83-409c-9c17-1a453d245934
redirect_from:
  - /2021080/docs/ht-replace-bundle-dependencies
  - /2021080/docs/en/ht-replace-bundle-dependencies
  - /docs/ht-replace-bundle-dependencies
  - /docs/en/ht-replace-bundle-dependencies
  - /v6/docs/ht-replace-bundle-dependencies
  - /v6/docs/en/ht-replace-bundle-dependencies
  - /v5/docs/ht-replace-bundle-dependencies
  - /v5/docs/en/ht-replace-bundle-dependencies
  - /v4/docs/ht-replace-bundle-dependencies
  - /v4/docs/en/ht-replace-bundle-dependencies
  - /v3/docs/ht-replace-bundle-dependencies
  - /v3/docs/en/ht-replace-bundle-dependencies
  - /v2/docs/ht-replace-bundle-dependencies
  - /v2/docs/en/ht-replace-bundle-dependencies
  - /v1/docs/ht-replace-bundle-dependencies
  - /v1/docs/en/ht-replace-bundle-dependencies
---

This document describes how to identify module dependencies and replace a dependent module with another one.

Each Spryker module might have several dependent modules that provide communication, utilities, and added functionality. Usually, adjustments are made by our plugin mechanism or class extensions. However, when introducing a massive functional change, you may need to replace an entire core module with one of your own or a 3rd party. To do so, there are two steps that you need to follow: replace the module and connect the modules to the new functionality.

{% info_block infoBox "Example" %}

A company working with the Payone and Refund modules decides to use a different refund functionality. They can replace the core refund module with their own implementation that satisfies the same interface. This requires replacing the existing refund module with a new refund implementation in the project code. Then, they must reroute the Payone module to communicate with the new refund functionality instead.

{% endinfo_block %}

## Prerequisites

The preceding example assumes that you know exactly what core module you want to replace. If that is not the case, you need to know what are the core module’s dependencies. You can find this information in a module’s `composer.json` file. This file lists all the dependent components and can be used to locate the dependent functionality that you want to replace based on your project’s requirements.

To replace a module with another module:

The following process describes adding a replace command into a new module to indicate that it replaces a core module.

For each module that you want to add, take these steps:

1. Replace the old module with the new one by creating a dummy module repository in a directory accessible to Composer.
    1. Name or rename the new module by using the old module’s name and prefixing it with `replace_`.  For example, create a dummy file called `replace_refund` to replace the refund module. This helps keep track of any replacements you do in the project.
    2. In the newly created dummy module directory, create an empty `composer.json` file and add the following Composer configuration information.
    3. Add the newly created module to your project’s `composer.json` file by going to `shop/composer.json` and adding the new location.
    4. Check if the core module is in your project’s `composer.json` file. If it is, remove it.
2. Execute the composer update command with the replacement module name: composer update `“replace_<the name of the module you are replacing>”`. Running the composer update command removes all mentions of the module (for example, `refund`) and replaces it with your module (for example, `replace_refund`).

{% info_block warningBox %}

For more information on using the composer replace, see [replace](https://getcomposer.org/doc/04-schema.md#replace) in official Composer documentation.

{% endinfo_block %}

## Composer configuration information

```
{
     "name": “<vendor>/ replace_<the name of the module you are replacing> ",
     "replace": {
       "spryker/<the name of the module you are replacing> ":"*"
     },
     "description": “<add_decription_of_what_you_are_replacing>"
    }
```

If you have added a replace module, go to `shop/vendor` and check that Composer has added the new `replace_ module/s` to this directory.

To check whether this has worked:

1. Go to `shop/vendor/spryker`.
2. Check that Composer has removed the modules that needed the replacement from the directory.
3. Connect the module with your new functionality.

## Set up a connection with the new functionality

Now that we have replaced a core module with a different module, we need to connect the rest of the OS to this new module.

To set up connectivity, check the replaced module’s usage and adapt its logic to the new module.

For further assistance on project-level implementations, email us: [support@spryker.com](mailto:support@spryker.com).
