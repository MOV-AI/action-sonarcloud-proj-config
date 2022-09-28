# Manages the repository's SonarCloud project

With this GitHub Action you can configure a SonarCloud project to run analisys triggered workflows execution.

## Usage

The workflow YAML file will usually look something like this:

```yaml
on:
  push:
    branches:
      - main

name: Main Workflow
jobs:
  sonarqube:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
      with:
        # Disabling shallow clone is recommended for improving relevancy of reporting
        fetch-depth: 0

    - name: Collect reports and run Sonar
      uses: MOV-AI/action-sonarcloud-proj-config@v1
      with:
        sonar_token: ${{ secrets.sonar_token }}
```

## Inputs

### Required
- `sonar_token` - SonarCloud token.

### Not required
- `sonar_org` (default: `${{ github.repository_owner }}`) - SonarCloud organization name.
