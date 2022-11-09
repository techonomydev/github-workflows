# Techonomy GitHub Workflows

Opinionated GitHub reusable workflow templates.

- Current production branch: `master`
- Newest versions (pip/poetry) branch: `next`

## Usage examples

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

  python:
    needs: frontend-build
    uses: techonomydev/github-workflows/.github/workflows/python-ci-e2e.yml@master
    with:
      name: my-project
      artifact_name: static
      artifact_path: src/bmy_project/static/bmy_project
      python_version: 3.9.13

```
