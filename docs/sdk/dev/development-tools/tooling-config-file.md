---
title: Tooling config file
description: The article provides information about a tooling config file that contains settings for supported tools and directives.
last_updated: Jun 16, 2021
template: concept-topic-template
originalLink: https://documentation.tooling-config-fileer.com/2021080/docs/tooling-config-file
originalArticleId: 535d6b07-76d8-47f1-a4d1-5b404439109e
redirect_from:
  - /2021080/docs/tooling-config-file
  - /2021080/docs/en/tooling-config-file
  - /docs/tooling-config-file
  - /docs/en/tooling-config-file
  - /v6/docs/tooling-config-file
  - /v6/docs/en/tooling-config-file
  - /v5/docs/tooling-config-file
  - /v5/docs/en/tooling-config-file
  - /v4/docs/tooling-config-file
  - /v4/docs/en/tooling-config-file
  - /v3/docs/tooling-config-file
  - /v3/docs/en/tooling-config-file
  - /v2/docs/tooling-config-file
  - /v2/docs/en/tooling-config-file
  - /docs/scos/dev/sdk/201811.0/development-tools/tooling-config-file.html
  - /docs/scos/dev/sdk/201903.0/development-tools/tooling-config-file.html
  - /docs/scos/dev/sdk/201907.0/development-tools/tooling-config-file.html
  - /docs/scos/dev/sdk/202001.0/development-tools/tooling-config-file.html
  - /docs/scos/dev/sdk/202005.0/development-tools/tooling-config-file.html
  - /docs/scos/dev/sdk/202009.0/development-tools/tooling-config-file.html
  - /docs/scos/dev/sdk/202108.0/development-tools/tooling-config-file.html
  - /docs/scos/dev/sdk/development-tools/tooling-config-file.html
related:
  - title: Architecture sniffer
    link: docs/scos/dev/sdk/development-tools/architecture-sniffer.html
  - title: Code sniffer
    link: docs/scos/dev/sdk/development-tools/code-sniffer.html
  - title: Formatter
    link: docs/scos/dev/sdk/development-tools/formatter.html
  - title: Performance audit tool- Benchmark
    link: docs/scos/dev/sdk/development-tools/performance-audit-tool-benchmark.html
  - title: PHPStan
    link: docs/scos/dev/sdk/development-tools/phpstan.html
  - title: SCSS linter
    link: docs/scos/dev/sdk/development-tools/scss-linter.html
  - title: TS linter
    link: docs/scos/dev/sdk/development-tools/ts-linter.html
  - title: Spryk code generator
    link: docs/scos/dev/sdk/development-tools/spryk-code-generator.html
  - title: Static Security Checker
    link: docs/scos/dev/sdk/development-tools/static-security-checker.html
---

In order to make the tool configuring more convenient, we introduce the `.tooling.yml` file. It contains settings for different tools (the Architecture and the Code sniffers are supported at the moment) in one place, helping you to keep the number of files on the root level as small as possible. The `.tooling.yml` file should also be in `.gitattributes` to be ignored for tagging:

```yml
... export-ignore
```

## Supported tools and directives

### Code sniffer

The code sniffer configuration section can have one directive: level. Example:

```yml
code-sniffer:
    level: 1
 ```

 ### Architecture sniffer

The architecture sniffer configuration section can have two directives: priority and ignoreErrors. Example:

```yml
architecture-sniffer:
    priority: 5
    ignoreErrors:
        - '#DependencyProvider#'
        - '#DevelopmentCommunicationFactory#'
```

Note that the keywords listed in the **ignoreErrors** directive are regular expressions. They are used to match the lines in the error list provided as a result of the architecture sniffer doing its job.
