# Qualcomm GitHub Organization

This repo contains workflow templates and other org level config and files

## Qualcomm Preflight Checks

Qualcomm repos should enable **Qualcomm Preflight Checks** upon creation. This workflow runs several preflight checks, including copyight, email, repolinter, and security checks. See [qualcomm/qcom-actions](https://github.com/qualcomm/qcom-actions) for details.

### Initial setup

1. Navigate to the new repo
1. Click on Actions
1. If you have existing actions in the repo, click "New workflow", else skip to next step
1. Locate the "By Qualcomm Technologies, Inc." section and click "Configure" under "Qualcomm Preflight Checks"
1. Click "Commit changes...", select "Commit directly to the main branch" (or feel free to create a new branch and start a PR), ensure your Qualcomm email is selected under "Commit Email", and then click "Sign off and commit changes"
1. This will create a GitHub Action config file in your repo under the path `.github/workflows/qcom-preflight-checks.yml`
1. See [qualcomm/qcom-actions](https://github.com/qualcomm/qcom-actions) for more information and how to disable checks.

### Repolinter Check: Customize Rules

> The `qcom-preflight-checks` workflow includes the Repolinter check.

When the Repolinter check runs, it first checks your Qualcomm repo for a local `repolint.json` file at the root directory. If it doesn't find one it'll use the default Qualcomm Repolinter ruleset, which is located here https://github.com/qualcomm/.github/blob/main/repolint.json

To customize the default Qualcomm Repolinter ruleset (e.g. to add some language specific file extensions for the license check), you can extend the default ruleset and override specific rules. In other cases you may have to copy the ruleset locally and edit as needed. See below for examples.

#### Exclude directories or files from the source file header check

For example, if we wanted to exclude the copyright/license check for a directory e.g. `/test-data` from Repolinter, we can extend the ruleset as we are adding additional rules.

1. Create the file `repolint.json` at the root of your project
1. "Extend" the Qualcomm repolint.json file

```json
{
  "extends": "https://raw.githubusercontent.com/qualcomm/.github/main/repolint.json",
  "rules": {}
}
```

3. Copy the rule block you need to adjust from `https://raw.githubusercontent.com/qualcomm/.github/main/repolint.json`. E.g. in this case we want to exclude `/test-data` from the license header check. So let's copy the json block `source-license-headers-exist` and paste it into the `rules` section of the local `repolint.json` we extended
1. Now lets add the `test-data` directory to the list of patterns to skip/exclude from being checked

```json
{
  "extends": "https://raw.githubusercontent.com/qualcomm/.github/main/repolint.json",
  "rules": {
    "source-license-headers-exist": {
      "level": "error",
      "rule": {
        "type": "file-starts-with",
        "options": {
          "globsAll": [
            "**/*.py",
            "**/*.js",
            "**/*.c",
            "**/*.cc",
            "**/*.cpp",
            "**/*.h",
            "**/*.ts",
            "**/*.sh",
            "**/*.rs",
            "**/*.java",
            "**/*.go",
            "**/*.bbclass",
            "**/*.S"
          ],
          "skip-paths-matching": {
            "patterns": [
              "babel.config.js",
              "build\/",
              "jest.config.js",
              "node_modules\/",
              "types\/",
              "uthash.h",
              "test-data\/"
            ]
          },
          "lineCount": 60,
          "patterns": [
            "(Copyright|©).*Qualcomm Innovation Center, Inc|Qualcomm Technologies, Inc|Copyright (\\(c\\)|©) (20(1[2-9]|2[0-2])(-|,|\\s)*)+ The Linux Foundation",
            "SPDX-License-Identifier|Redistribution and use in source and binary forms, with or without"
          ],
          "flags": "i"
        }
      }
    }
  }
}
```

#### Include only specific directories or files in the source file header check

For example, to only check `.c` files in a specific directory (e.g., `/src`) in the copyright/license check using Repolinter, we cannot extend and must instead replace the ruleset and edit it as necessary.

1. Copy the default Qualcomm [repolint.json](https://raw.githubusercontent.com/qualcomm/.github/main/repolint.json) ruleset to the root of your project
2. Find the relevant rule to edit. In this example, we are going to edit the `source-license-headers-exist` rule and replace the `globsAll` property to only `.c` files in the `/src` directory.

```json
[...]
    "source-license-headers-exist": {
      "level": "error",
      "rule": {
        "type": "file-starts-with",
        "options": {
          "globsAll": [
            "src/**/*.c"
          ],
          "skip-paths-matching": {
            "patterns": []
          },
          "lineCount": 60,
          "patterns": [
            "(Copyright|©).*Qualcomm Innovation Center, Inc|Qualcomm Technologies, Inc|Copyright (\\(c\\)|©) (20(1[2-9]|2[0-2])(-|,|\\s)*)+ The Linux Foundation",
            "SPDX-License-Identifier|Redistribution and use in source and binary forms, with or without"
          ],
          "flags": "i"
        }
      }
    },
[...]    
```

3. For more information on Repolinter rules and options, see [Repolinter rules](https://github.com/todogroup/repolinter/blob/main/docs/rules.md)
