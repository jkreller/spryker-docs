---
title: Data Transformer Collate Filter Range
description: This document provides details about the Data Transformer Collate Filter Range service in the Components Library.
template: concept-topic-template
related:
  - title: Data Transformer Filters
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/data-transformers/collate/filters/index.html
  - title: Data Transformer Collate Filter Equals
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/data-transformers/collate/filters/equals.html
  - title: Data Transformer Collate Filter Text
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/data-transformers/collate/filters/text.html
---

This document explains the Data Transformer Collate Filter Range service in the Components Library.

## Overview

Data Transformer Collate Filter Range is an Angular Service that implements filtering to range of data values based on configuration.

Check out an example usage of the Data Transformer Collate Filter Range in the `@spryker/table` config:

```html
<spy-table
    [config]="{
        datasource: {
            ...,                                               
            transform: {
                ...,
                filter: {
                    select1: {
                        type: 'range',
                        propNames: 'col1',
                    },
                    select2: {
                        type: 'range',
                        propNames: ['col2', 'col1'],
                    },
                },
            },
        },
    }"
>
</spy-table>
```

## Service registration

Register the service:

```ts
declare module '@spryker/data-transformer.collate' {
    interface DataTransformerFilterRegistry {
        range: RangeDataTransformerFilterService;
    }
}

@NgModule({
    imports: [
        DataTransformerModule.withTransformers({
            collate: CollateDataTransformerService,
        }),
        CollateDataTransformer.withFilters({
            range: RangeDataTransformerFilterService,
        }),
    ],
})
export class RootModule {}
```

## Interfaces

Below you can find interfaces for the Data Transformer Collate Filter Range:

```ts
interface DataTransformerFilterConfig {
    type: string;
    propNames: string | string[];
}
```
