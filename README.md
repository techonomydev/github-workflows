# Techonomy GitHub Workflows

Opinionated GitHub reusable workflow templates.

- Current production branch: `main`
- Newest versions (pip/poetry) branch: `next`

## Usage examples

```yaml
name: CI

on:
  push:
    branches:
      - master
      - main
  pull_request:
    branches:
      - master
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
      artifact_path: src/bmy_project/static/bmy_project
      python_version: 3.11

```
