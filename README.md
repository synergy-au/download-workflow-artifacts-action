# Download Previous Workflow's Artifacts
GitHub Action that allows you to download artifacts generated from the previous workflow that triggered a `workflow_run` event on another workflow. This will download and unzip the artifacts in the directory of where the action is running from.

## Example Workflow File

```yaml
name: Example Workflow

on:
  workflow_run:
    workflows: ["Previous Workflow"]
    types: 
      - completed

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout Repository
      uses: actions/checkout@v3
    - name: Download Artifacts from Previous Workflow
      uses: synergy-au/download-workflow-artifacts-action@v1
```
