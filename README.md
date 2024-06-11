- [Git Pre-commit Framework](#git-pre-commit-framework)
  - [Aliases](#aliases)
  - [Using homebrew](#using-homebrew)
  - [GitGuardian](#gitguardian)
  - [Helm Docs](#helm-docs)

### Git Pre-commit Framework
- [pre-commit.com](https://pre-commit.com/)

#### Aliases
```
alias pcinstall='pre-commit install'
```
```
alias pcuninstall='pre-commit uninstall'
```
```
alias pcall='pre-commit run --all-files'
```
```
alias pcup='pre-commit autoupdate'
```

#### Using homebrew
```
brew install pre-commit
```

#### GitGuardian
- `.env` file in the repo for scanning with the GitGuardian API key
- Remember to add `.env` to `.gitignore`

```
GITGUARDIAN_API_KEY=<crazy long string of numbers and letters>
```

#### Helm Docs

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
