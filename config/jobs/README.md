# Jobs Configuration

This directory contains Prow job configurations for the cert-manager/testing repository.

## Structure

```
jobs/
├── cert-manager/
│   ├── testing/
│   │   └── testing-presubmits.yaml
│   └── cert-manager/
│       └── cert-manager-presubmits.yaml
└── README.md
```

## Job Types

### Presubmit Jobs

Presubmit jobs run against pull requests before they are merged. They are defined
in `*-presubmits.yaml` files.

### Postsubmit Jobs

Postsubmit jobs run after a pull request is merged. They are defined in
`*-postsubmits.yaml` files.

### Periodic Jobs

Periodic jobs run on a schedule. They are defined in `*-periodics.yaml` files.

## Adding a New Job

1. Identify the appropriate directory for your job based on the repository it targets.
2. Create or modify the appropriate YAML file.
3. Follow the existing job format and conventions.
4. Run `make verify` to validate your configuration.
5. Run `make generate` if you added any new job templates that require generated output.

## Autobumping

Job configurations are automatically bumped when new versions of test images are
released. The autobump configuration is located at
`config/autobump-config/testing-autobump-config.yaml`.

The autobumper will open a pull request with updated image tags whenever a new
image is pushed to the registry.

## Validation

All job configurations are validated using the Prow job configuration validator.
Run `make verify` to validate all configurations locally before submitting a PR.

> **Note (personal fork):** I use `make verify` and `make generate` together as
> a habit before pushing any changes. Keeping this note here as a reminder.
