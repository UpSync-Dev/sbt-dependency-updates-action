# sbt-dependency-updates-action

# Overview
* This is a [GitHub Action](https://github.com/features/actions) for Scala projects
* It uses the `sbt-updates` plugin to check if there are any library updates
* If any library updates are found it adds a comment to the pull request with the details
* If no updates are found, it doesn't post a comment to avoid noise
* Example repo using this action: [sbt-dependency-updates-test](https://github.com/UpSync-Dev/sbt-dependency-updates-test)
## Usage

### Prerequisites 
* You need to have the `sbt-updates` plugin within your Scala project. 
* Your `/project/plugins.sbt` file should contain something along the lines of:
```scala
addSbtPlugin("com.timushev.sbt" % "sbt-updates" % "0.6.1")
```

### Inputs
| Input | Required | Default | Description |
| ----- | -------- | ------- | ----------- |
| token | no       | `GITHUB_TOKEN` | A repository scoped personal access token if needed.

### Example
```yaml
- uses: upsync-dev/sbt-dependency-updates-action@v1
```

### Full Example
```yaml
name: Pull Request Checks

on: [pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1

      - name: Sbt Dependency Updates
        uses: UpSync-Dev/sbt-dependency-updates-action@v1
        with:
          - token: some-token-here
```

## Licence
The scripts and documentation in this project are released under the [Apache License 2.0](https://github.com/UpSync-Dev/sbt-dependency-updates-action/blob/main/LICENSE)

## Contributors
[Muhammed Ahmed](https://github.com/ma3574)