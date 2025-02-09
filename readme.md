# Cleanup Cache Action

This GitHub Action cleans up dependency caches to save space.

## Description

The `Cleanup Cache` action removes dependency caches for various package managers to free up disk space.

## Inputs

- `package_manager` (required): The package manager used (npm, yarn, pip, etc.)

## Usage

```yaml
name: Cleanup Cache Workflow
on: [push]

jobs:
  cleanup-cache:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Cleanup Cache
        uses: ./actions/cleanup-cache-action
        with:
          package_manager: 'npm'

      - name: Nest CI Action
        uses: ./actions/nest-ci-action
        with:
          package_manager: 'npm'
```

# NestJS CI Action

This GitHub Action installs dependencies, runs tests, and builds the NestJS application.

## Description

The `NestJS CI` action sets up a Node.js environment, installs dependencies, runs tests using Jest, and builds the NestJS application.

## Inputs

- `node_version` (optional): Node.js version to use. Default is `18`.
- `install_command` (optional): Command to install dependencies (`npm install` or `yarn install`). Default is `npm install`.

## Usage

```yaml
name: NestJS CI Workflow
on: [push]

jobs:
  nestjs-ci:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: NestJS CI
        uses: ./actions/nest-ci-action
        with:
          node_version: '18'
          install_command: 'npm install'