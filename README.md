# Harness STO Global Configuration Manager
Starter repository for the Harness STO Configuration Manager plugin

## Summary

The purpose of this repository is to contain Harness Security Test Orchestration configuration overrides and tuning. This repository used in conjunction with the  based on a hierarchical which means a layered approach can be applied to support the various layers of Harness structure (Account->Organization->Project->Pipeline).

## Repository Folder and File layout
Global Configurations are controlled with individual YAML files stored at the root of the repository using the convention `scanner.yaml` - e.g To create a configuration manager for OWASP Dependency Check, the file name should be `owasp.yaml`

### Override for all resources in an specified organization
1. Create a new folder in the `overrides` directory named for the `organization_id`
2. For each scanner requiring a configuration override, create a file named for the scanner - e.g. `owasp.yaml`

### Override for all resources in an specified project within an organization_id
1. Create a new folder in the `overrides` directory named for the `organization_id`
2. Create a new folder in the `overrides/organization_id` directory named for the `project_id`
3. For each scanner requiring a configuration override, create a file named for the scanner - e.g. `owasp.yaml`

### Override for all resources in an specified pipeline within an organization_id/project_id
1. Create a new folder in the `overrides` directory named for the `organization_id`
2. Create a new folder in the `overrides/organization_id` directory named for the `project_id`
2. Create a new folder in the `overrides/organization_id/project_id` directory named for the `pipeline_id`
3. For each scanner requiring a configuration override, create a file named for the scanner - e.g. `owasp.yaml`

## Override File Format
The following keys are supported in your override files.

_Note: Each file should be named using the name of the Harness STO scanner type_

Example File:
```
---
binaries:
  yarn: /shared/customer_artifacts/tools/yarn
  pnpm: /shared/customer_artifacts/tools/pnpm
exclusions:
  - "**/*.exe"
standard_args:
  - --verbose
  - --log-opts="-n 400"
remove_files:
  - "**/yarn.lock"
```

### Binaries
Some scanners require that the path to binaries are known when running the scanner. Additionally, these binaries must exist in a files system accessible to the scanner. The Key in this case is the name of the binary while the value will be the path to the binary.

Example:
```
binaries:
  yarn: /shared/customer_artifacts/tools/yarn
  pnpm: /shared/customer_artifacts/tools/pnpm
```

### Exclusions
Exclusions are a list of files, partial file names with wildcards, or entire directories that should not be scanned. Each entry is prefixed with the argument `--exclude`

Example:
```
exclusions:
  - "**/*.exe"
```

### Remove Files
Occassionally, the existence of certain files in a repository can cause issues for scanners. This process will remove those files from the local repository prior to running the scanners

Example:
```
remove_files:
  - "**/yarn.lock"
```

### Standard Arguments
A list of cli arguments to pass. The entire line is passed as the list is collapsed into a space delimited string for each element.

Example:
```
standard_args:
  - --exit-code 999
  - --no-banner
  - --redact
```

## Contributing

A complete [Contributors Guide](CONTRIBUTING.md) can be found in this repository

## Authors

Module is maintained by Harness, Inc

## License

MIT License. See [LICENSE](LICENSE) for full details.
