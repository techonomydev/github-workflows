# Techonomy GitHub Workflows

Opinionated GitHub reusable workflow templates.

- Current production branch: `main`
- Newest versions (pip/poetry) branch: `next`

## Usage examples

Python project with frontend and E2E tests.

```yaml
name: CI

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  frontend:
    uses: techonomydev/github-workflows/.github/workflows/frontend-ci.yml@main
    with:
      working_directory: frontend
      node_version: 18

  python:
    needs: frontend-build
    uses: techonomydev/github-workflows/.github/workflows/python-ci-e2e.yml@main
    with:
      name: my-project
      artifact_name: static
      artifact_path: src/my_project/static/my_project
      python_version: 3.11
```

Publish a Python package.

```yaml
name: Publish package

on:
  release:
    types: ["published"]
  workflow_dispatch:

jobs:
  frontend:
    uses: techonomydev/github-workflows/.github/workflows/frontend-ci.yml@main
    with:
      working_directory: frontend
      node_version: 18

  python:
    needs: python-publish-package
    uses: techonomydev/github-workflows/.github/workflows/python-publish-package.yml@main
    with:
      name: my-project
      artifact_name: static
      artifact_path: src/my_project/static/my_project
      python_version: 3.11
```
