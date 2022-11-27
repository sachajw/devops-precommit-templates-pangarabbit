# Git Pre-commit Framework
- [pre-commit.com](https://pre-commit.com/)

#### Installation
- Before you can run hooks, you need to have the pre-commit package manager installed.
#### Using pip:
```
pip install pre-commit
```
- In a python project, add the following to your requirements.txt (or requirements-dev.txt):
```
pre-commit
```
#### As a 0-dependency zipapp
- locate and download the .pyz file from the github releases
- run python pre-commit-#.#.#.pyz ... in place of pre-commit ...

#### Using homebrew
```
brew install pre-commit
```
#### Using conda (via conda-forge)
```
conda install -c conda-forge pre-commit
```
`.env` example for GitGuardian API key
```
GITGUARDIAN_API_KEY=<crazy long string of numbers and letters>
```
`linter_values.yaml` example required for Helm Docs
```
dockerRegistry: ".dkr.ecr.eu-central-1.amazonaws.com"
accountPrefix:
regionShort:
blueGreenValue: blue

clusterNameTemplate: |-
  {{ print .Values.regionShort "-" | trimPrefix "ec1-" }}{{ include "account.name" . }}-{{ .Values.blueGreenValue }}
accounts:
  infra:
    id: ""
  nonprod:
    id: ""
  preprod:
    id: ""
  prod:
    id: ""
  common:
    id: ""

stages:
  test: ""
    account: nonprod
  playground:
    account: infra

vault:
  address:

filebeat:
  image:
    registry:  .dkr.ecr.eu-central-1.amazonaws.com
    repository: tools/filebeat
    tag: 7.12.1

dynatrace:
  groupnamePrefix:
```
