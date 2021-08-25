# Download Previous Workflow's Artifacts
GitHub Action that allows you to download artifacts generated from the previous workflow that triggered a `workflow_run` event on another workflow. This will download and unzip the artifacts in the directory of where the action is running from.

## Example Workflow File
```
name: Example Flow
on:
  workflow_run:
    workflows: ["Previous Flow"]
    types: 
      - completed
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout Repository
      uses: actions/checkout@v2.3.4
    - name: Download Artifacts from Previous Workflow
      uses: synergy-au/download-workflow-artifacts-action@v1
      with:
        # Only needed for private repos
        auth-token: ${{ secrets.GITHUB_TOKEN }}
        # You can get this from the workflow_run event. A workflow run ID is required.
        workflow-run-id: ${{ github.event.workflow_run.id }}
```
