<!-- markdownlint-disable -->
<a href="https://cpco.io/homepage"><img src=".github/banner.png?raw=true" alt="Project Banner"/></a><br/>
    <p align="right">
<a href="https://github.com/cloudposse-github-actions/readme/releases/latest"><img src="https://img.shields.io/github/release/cloudposse-github-actions/readme.svg" alt="Latest Release"/></a><a href="https://slack.cloudposse.com"><img src="https://slack.cloudposse.com/badge.svg" alt="Slack Community"/></a></p>
<!-- markdownlint-restore -->

<!--




  ** DO NOT EDIT THIS FILE
  **
  ** This file was automatically generated by the `cloudposse/build-harness`.
  ** 1) Make all changes to `README.yaml`
  ** 2) Run `make init` (you only need to do this once)
  ** 3) Run`make readme` to rebuild this file.
  **
  ** (We maintain HUNDREDS of open source projects. This is how we maintain our sanity.)
  **





-->

Rebuilds [`README.md`](README.md) and associated banners from templates using the [`README.yaml`](README.yaml) metadata.



---
> [!NOTE]
> This project is part of Cloud Posse's comprehensive ["SweetOps"](https://cpco.io/homepage?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=) approach towards DevOps.
> <details><summary><strong>Learn More</strong></summary>
>
> It's 100% Open Source and licensed under the [APACHE2](LICENSE).
>
> We have [*dozens of GitHub Actions*](https://github.com/cloudposse-github-actions?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=github_actions) that are Open Source and well-maintained. Check them out!
> </details>

<a href="https://cloudposse.com/readme/header/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=readme_header_link"><img src="https://cloudposse.com/readme/header/img"/></a>


## Introduction

This opinionated implementation builds upon Cloud Posse's build-harness and README.yaml
used throughout Cloud Posse's GitHub repositories.



## Usage



> [!IMPORTANT]
> In Cloud Posse's examples, we avoid pinning GitHub Actions to specific versions to prevent discrepancies between the documentation 
> and the latest released versions. However, for your own projects, we strongly advise pinning each GitHub Action to the exact version
> you're using. This practice ensures the stability of your workflows. Additionally, we recommend implementing a systematic 
> approach for updating versions to avoid unexpected changes.



To use this project, follow these steps:

Add the following code to your workflow file (e.g., `.github/workflows/readme.yml`):

```yaml
name: README
on:
  pull_request:
    branches: [ 'main' ]
    types: [opened, synchronize, reopened, closed, labeled, unlabeled]

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Rebuild README.md and Banner
        uses: cloudposse-github-actions/readme@v0
        id: readme
        with:
          banner_enabled: true
          readme_enabled: true

    outputs:
      result: ${{ steps.readme.outputs.result1 }}
```

## Advanced Usage

In the following example, we use the `workflow_dispatch` event to allow manual triggering of the workflow to rebuild the readme.  
We also use the `pull_request` event to register the workflow from the PR. This allows us to test the workflow before merging
it to the main branch.

```yaml
  name: README
  on:
    # Allow manual triggering of workflow to rebuild readme
    workflow_dispatch: {}

    ## Added pull_request to register workflow from the PR.
    ## Read more https://stackoverflow.com/questions/63362126/github-actions-how-to-run-a-workflow-created-on-a-non-master-branch-from-the-wo
    pull_request:
      branches-ignore: ['*']

  schedule:
    # Update README.md nightly at 4am UTC
    #         .---------------- minute (0 - 59)
    #         |  .------------- hour (0 - 23)
    #         |  |  .---------- day of month (1 - 31)
    #         |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
    #         |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
    #         |  |  |  |  |
    - cron:  '0  4  *  *  *'

  jobs:
    generate:
      runs-on: ubuntu-latest
      steps:
        - name: Rebuild README.md and Banner
          uses: cloudposse-github-actions/readme@v0
          id: readme
          with:
            banner_enabled: true
            readme_enabled: true
```






<!-- markdownlint-disable -->

## Inputs

| Name | Description | Default | Required |
|------|-------------|---------|----------|
| banner\_enabled | banner\_enabled | true | false |
| commit\_author | The author to use when committing changes. | readme-action 📖 <actions@github.com> | false |
| commit\_message | The commit message to use when committing changes. | chore: update README.md and docs | false |
| commit\_method | The method to apply changes. Can be either 'commit' or 'pr'. | commit | true |
| commit\_user\_email | The user email to use when committing changes. | actions@github.com | false |
| commit\_user\_name | The user name to use when committing changes. | readme-action 📖 | false |
| pr\_base\_branch | Repo default base-branch for Pull Requests (when commit\_method: pr) |  | false |
| pr\_labels | Whitespace-separated list of labels to apply to Pull Requests (when commit\_method: pr) | auto-update<br>no-release<br>readme<br> | false |
| pr\_title | The title to use when creating a Pull Request (when commit\_method: pr) | Update README.md and docs | false |
| readme\_enabled | readme\_enabled | true | false |
| repository\_description | repository\_description |  | false |
| repository\_name | repository\_name |  | false |
| repository\_org | GitHub organization or user name used for the banner templates |  | false |
| token | GitHub API token (use a PAT if you need to trigger other actions) | ${{ github.token }} | false |
| validate\_readme | Validate the README.md file using markdown-link-check | true | false |


## Outputs

| Name | Description |
|------|-------------|
| banner\_file | Generated banner file path (if banner\_enabled: true) |
| readme\_file | Generated README file path (if readme\_enabled: true) |
<!-- markdownlint-restore -->


## Related Projects

Check out these related projects.



## References

For additional context, refer to some of these links.

- [screenshot](https://github.com/cloudposse-github-actions/screenshot) - 


## ✨ Contributing

This project is under active development, and we encourage contributions from our community.
Many thanks to our outstanding contributors:

<a href="https://github.com/cloudposse-github-actions/readme/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=cloudposse-github-actions/readme&max=24" />
</a>

### 🐛 Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse-github-actions/readme/issues) to report any bugs or file feature requests.

### 💻 Developing

If you are interested in being a contributor and want to get involved in developing this project or help out with Cloud Posse's other projects, we would love to hear from you! 
Hit us up in [Slack](https://cpco.io/slack?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=slack), in the `#cloudposse` channel.

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.
 1. Review our [Code of Conduct](https://github.com/cloudposse-github-actions/readme/?tab=coc-ov-file#code-of-conduct) and [Contributor Guidelines](https://github.com/cloudposse/.github/blob/main/CONTRIBUTING.md).
 2. **Fork** the repo on GitHub
 3. **Clone** the project to your own machine
 4. **Commit** changes to your own branch
 5. **Push** your work back up to your fork
 6. Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!

### 🌎 Slack Community

Join our [Open Source Community](https://cpco.io/slack?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=slack) on Slack. It's **FREE** for everyone! Our "SweetOps" community is where you get to talk with others who share a similar vision for how to rollout and manage infrastructure. This is the best place to talk shop, ask questions, solicit feedback, and work together as a community to build totally *sweet* infrastructure.

### 📰 Newsletter

Sign up for [our newsletter](https://cpco.io/newsletter?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=newsletter) and join 3,000+ DevOps engineers, CTOs, and founders who get insider access to the latest DevOps trends, so you can always stay in the know.
Dropped straight into your Inbox every week — and usually a 5-minute read.

### 📆 Office Hours <a href="https://cloudposse.com/office-hours?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=office_hours"><img src="https://img.cloudposse.com/fit-in/200x200/https://cloudposse.com/wp-content/uploads/2019/08/Powered-by-Zoom.png" align="right" /></a>

[Join us every Wednesday via Zoom](https://cloudposse.com/office-hours?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=office_hours) for your weekly dose of insider DevOps trends, AWS news and GitHub Action insights, all sourced from our SweetOps community, plus a _live Q&A_ that you can’t find anywhere else.
It's **FREE** for everyone!

## About

This project is maintained by <a href="https://cpco.io/homepage?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=">Cloud Posse, LLC</a>.
<a href="https://cpco.io/homepage?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content="><img src="https://cloudposse.com/logo-300x69.svg" align="right" /></a>

We are a [**DevOps Accelerator**](https://cpco.io/commercial-support?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=commercial_support) for funded startups and enterprises.
Use our ready-to-go terraform architecture blueprints for AWS & GitHub Actions to get up and running quickly.
We build it with you. You own everything. Your team wins. Plus, we stick around until you succeed.

<a href="https://cpco.io/commercial-support?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=commercial_support"><img alt="Learn More" src="https://img.shields.io/badge/learn%20more-success.svg?style=for-the-badge"/></a>

*Your team can operate like a pro today.*

Ensure that your team succeeds by using our proven process and turnkey blueprints. Plus, we stick around until you succeed.

<details>
  <summary>📚 <strong>See What's Included</strong></summary>

- **Reference Architecture.** You'll get everything you need from the ground up built using 100% infrastructure as code.
- **Deployment Strategy.** You'll have a battle-tested deployment strategy using GitHub Actions that's automated and repeatable.
- **Site Reliability Engineering.** You'll have total visibility into your apps and microservices.
- **Security Baseline.** You'll have built-in governance with accountability and audit logs for all changes.
- **GitOps.** You'll be able to operate your infrastructure via Pull Requests.
- **Training.** You'll receive hands-on training so your team can operate what we build.
- **Questions.** You'll have a direct line of communication between our teams via a Shared Slack channel.
- **Troubleshooting.** You'll get help to triage when things aren't working.
- **Code Reviews.** You'll receive constructive feedback on Pull Requests.
- **Bug Fixes.** We'll rapidly work with you to fix any bugs in our projects.
</details>

<a href="https://cloudposse.com/readme/commercial-support/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=readme_commercial_support_link"><img src="https://cloudposse.com/readme/commercial-support/img"/></a>
## License

<a href="https://opensource.org/licenses/Apache-2.0"><img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=for-the-badge" alt="License"></a>

<details>
<summary>Preamble to the Apache License, Version 2.0</summary>
<br/>
<br/>

Complete license is available in the [`LICENSE`](LICENSE) file.

```text
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

  https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
```
</details>

## Trademarks

All other trademarks referenced herein are the property of their respective owners.
---
Copyright © 2017-2024 [Cloud Posse, LLC](https://cpco.io/copyright)


<a href="https://cloudposse.com/readme/footer/link?utm_source=github&utm_medium=readme&utm_campaign=cloudposse-github-actions/readme&utm_content=readme_footer_link"><img alt="README footer" src="https://cloudposse.com/readme/footer/img"/></a>

<img alt="Beacon" width="0" src="https://ga-beacon.cloudposse.com/UA-76589703-4/cloudposse-github-actions/readme?pixel&cs=github&cm=readme&an=readme"/>
