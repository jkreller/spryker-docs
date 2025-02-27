---
title: Actions Refresh Parent Table
description: This document provides details about the Actions Refresh Parent Table service in the Components Library.
template: concept-topic-template
related:
  - title: Actions
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/actions/index.html
  - title: Actions Close Drawer
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/actions/actions-close-drawer.html
  - title: Actions Drawer
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/actions/actions-drawer.html
  - title: Actions HTTP
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/actions/actions-http.html
  - title: Actions Notification
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/actions/actions-notification.html
  - title: Actions Redirect
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/actions/actions-redirect.html
  - title: Actions Refresh Drawer
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/actions/actions-refresh-drawer.html
  - title: Actions Refresh Table
    link: docs/marketplace/dev/front-end/page.version/ui-components-library/actions/actions-refresh-table.html

---

This document explains the Actions Refresh Parent Table service in the Components Library.

## Overview

Actions Refresh Parent Table is an Angular Service that refreshes the data of the parent table of a Table in the current context.

{% info_block warningBox "Note" %}

Make sure that the table opened from another table, for ex. in the Drawer.

{% endinfo_block %}

Check out an example usage of the Actions Refresh Parent Table.

Service configuration:

- `rowActions`—the table row actions. For more details, see [Table Feature Row Actions](/docs/marketplace/dev/front-end/{{page.version}}/table-design/table-features/table-feature-row-actions.html).  
- `actions`—an array with actions configuration.  
- `type`—an action type.  

```html
<spy-table
    [config]="{
        dataSource: { ... },
        columns: [ ... ],
        rowActions: {
            enabled: true,
            actions: [
                {
                    type: 'refresh-parent-table',
                },
            ],
        },
    }"
>
</spy-table>
```

## Service registration

Register the service:

```ts
declare module '@spryker/actions' {
    interface ActionsRegistry {
        'refresh-parent-table': RefreshParentTableActionHandlerService;
    }
}

@NgModule({
    imports: [
        ActionsModule.withActions({
            'refresh-parent-table': RefreshParentTableActionHandlerService,
        }),
    ],
})
export class RootModule {}
```

## Interfaces

Below you can find interfaces for the Actions Refresh Parent Table:

```ts
export interface RefreshParentTableActionConfig extends ActionConfig {}
```
