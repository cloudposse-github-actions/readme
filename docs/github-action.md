<!-- markdownlint-disable -->

## Inputs

| Name | Description | Default | Required |
|------|-------------|---------|----------|
| banner\_enabled | Enable banner generation | true | false |
| commit\_author | The author to use when committing changes. | readme-action 📖 <actions@github.com> | false |
| commit\_message | The commit message to use when committing changes. | chore: update README.md | false |
| commit\_method | The method to apply changes. Can be either 'commit' or 'pr'. | commit | true |
| commit\_push\_options | The push options to use when committing changes. Use --force-with-lease to avoid overwriting changes when pushing<br>to a protected branch using admin or bypass privileges. See https://git-scm.com/docs/git-push#\_options for more.<br> |  | false |
| commit\_user\_email | The user email to use when committing changes. | actions@github.com | false |
| commit\_user\_name | The user name to use when committing changes. | readme-action 📖 | false |
| pr\_base\_branch | Repo default base-branch for Pull Requests (when commit\_method: pr) |  | false |
| pr\_branch | Branch to create Pull Requests from (when commit\_method: pr). Suggest using a protected branch for auto-merge capabilities. | auto-update/readme | false |
| pr\_labels | Whitespace-separated list of labels to apply to Pull Requests (when commit\_method: pr) | auto-update<br>no-release<br>readme<br> | false |
| pr\_title | The title to use when creating a Pull Request (when commit\_method: pr) | Update README.md and docs | false |
| readme\_enabled | Enable README generation | true | false |
| repository\_description | GitHub repository description |  | false |
| repository\_name | GitHub repository name in the `repository\_org` that hosts the banner templates |  | false |
| repository\_org | GitHub organization or user name used for the banner templates |  | false |
| token | GitHub API token (use a PAT if you need to trigger other actions) | ${{ github.token }} | false |
| validate\_readme | Validate the README.md file using markdown-link-check | true | false |


## Outputs

| Name | Description |
|------|-------------|
| banner\_file | Generated banner file path (if banner\_enabled: true) |
| readme\_file | Generated README file path (if readme\_enabled: true) |
<!-- markdownlint-restore -->
