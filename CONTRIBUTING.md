# Contributing to this Project
Harness values the input and feedback from our community of users.  This repository is open to fork and update via Pull Requests

## Style Guidelines
This project includes support for the auto-formatting tool known as [EditorConfig](https://EditorConfig.org) (File://.editorconfig).  This is a plugin for most modern IDE platforms such as Visual Studio Code (preferred by the maintainers) among others.  It is highly suggested to leverage this tool as part of your contributions as it will help to ensure proper and clear spacing and formatting of files for consistency.

When contributing to this project, please adhere to the following guidelines:
* Indentation Guidelines per file type

    | File Type | Indentation Type | Indentation Size |
    | --- | --- | --- |
    | `.tf` | Spaces | 2 |
    | `.yml` | Spaces | 2 |
    | `.yaml` | Spaces | 2 |
    | `Makefile`| Tab | 4 |
    | `*.*` | Spaces | 4 |

* Use linux-style file endings (`lf`) for all git commits to ensure consistency across platforms
* Character Set should be `utf-8`
* Leverage the [terraform fmt](https://developer.hashicorp.com/terraform/cli/commands/fmt) command to auto-format Terraform files to help automatically align Terraform file indentation for consistency.

## Documentation Requirements
Each module and associated variables need to be clearly and descriptively documented indicating their purpose and expected value types.  In addition, example snippets should be shared to show how the module can be leveraged in Terraform templates.
