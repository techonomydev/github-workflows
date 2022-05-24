# Techonomy GitHub Workflows

Opinionated GitHub reusable workflow templates.

## Usage

```yaml
name: CI

on:
  push:
    branches: [master]
  pull_request:
    branches: [master]

jobs:
  frontend:
    uses: techonomydev/github-workflows/.github/workflows/frontend-ci.yml@master
    with:
      working_directory: frontend
      node_version: 16.14
```
