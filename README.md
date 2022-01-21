# mfe-run-journey-tests-action
This is a GitHub Action meant to be used as a [composite action](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action) within an existing workflow. This action allows you to run testcafe journey tests on your MFE against a given host.

## Inputs

### `journey-test-host`

**Required** The full URL of the host you want to run your journey tests against.

### `journey-test-directory`

**Required** The directory which holds your testcafe tests.

### `journey-test-browser`

**Required** The browser you wish to run your journey tests in (`chromium` or `firefox`)

### `journey-test-host-username`

**Required** If your host requires a username and password, pass the username here.

### `journey-test-host-password`

**Required** If your host requires a username and password, pass the password here.

## Usage
You can use this composite Action in your own workflow by adding:

```yml
name: composite

on:
  push:
    branches: [ master ]

  workflow_dispatch:

jobs:
  ci_job:
    runs-on: ubuntu-latest
    steps:
      - name: Run journey tests
        uses: awazevr/mfe-run-journey-tests-action@v1.0.0
        with:
          journey-test-host: https://www.example.com/
          journey-test-directory: __tests__/journey
          journey-test-browser: chromium
          journey-test-host-username: username
          journey-test-host-password: password

```

