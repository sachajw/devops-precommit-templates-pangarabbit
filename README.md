[Git Pre-commit Framework](#git-pre-commit-framework)

- [Git Pre-commit Framework](#git-pre-commit-framework)
  - [Aliases](#aliases)
  - [Install Pre-commit with Homebrew](#install-pre-commit-with-homebrew)
- [Frigate](#frigate)
- [GitGuardian](#gitguardian)
- [Helm Docs](#helm-docs)
- [KubeConform](#kubeconform)

### Git Pre-commit Framework

[Pre-commit.com](https://pre-commit.com/)

#### Aliases

```shell
alias pcinstall='pre-commit install'
```

```shell
alias pcuninstall='pre-commit uninstall'
```

```shell
alias pcall='pre-commit run --all-files'
```

```shell
alias pcup='pre-commit autoupdate'
```

#### Install Pre-commit with Homebrew

```shell
brew install pre-commit
```

### Frigate

[Frigate](https://frigate.readthedocs.io/en/latest/)

```yaml
repos:
- repo: https://github.com/rapidsai/frigate/
   rev: v0.4.0 #  pre-commit autoupdate  - to keep the version up to date
   hooks:
      - id: frigate
      args:
      - --output=README.rst
      - --format=rst
      - --no-credits
      - --no-deps
```

### GitGuardian

[GitGuardian.com](https://www.gitguardian.com/)

- `.env` file in the repo for scanning with the GitGuardian API key
- Remember to add `.env` to `.gitignore`

```shell
GITGUARDIAN_API_KEY=<crazy long string of numbers and letters>
```

### Helm Docs

[Helm Docs](https://github.com/norwoodj/helm-docs)

`linter_values.yaml` example required for Helm Docs

```yaml
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

### KubeConform

[KubeConform](https://github.com/yannh/kubeconform)