# guix-systole-check-commit-message-action

This GitHub composite action verifies that commit messages conform to the
[guix-systole guidelines](https://github.com/SystoleOS/guix-systole/blob/main/README.md)
guidelines.

## Usage

To automatically enforce the guix-systole commit message style during pull requests or
pushes to the `main` branch, create a workflow file at
`.github/workflows/commit-message.yml` with the following content:

```yaml
name: "Commit Message Check"
on:
  pull_request:
    types:
      - opened
      - edited
      - reopened
      - synchronize
  push:
    branches:
      - main

permissions:
  contents: read
  pull-requests: read

jobs:
  check-commit-message:
    runs-on: ubuntu-latest
    steps:
      - name: Check Commit Message
        uses: SystoleOS/guix-systole-check-commit-message-action@v1.0.0
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
```

This workflow will trigger commit message checks on relevant pull request events
or when changes are pushed to the `main` branch.

## History
- This repository is a fork of https://github.com/Slicer/slicer-check-commit-message-action

- This action was originally implemented by
[@jamesobutler](https://github.com/jamesobutler),
[@pieper](https://github.com/pieper) and [@jcfr](https://github.com/jcfr) in the
Slicer repository under `.github/workflows/commit-message.yml`.
