# `github-release`

[![GitHub release](https://img.shields.io/github/release/maurobringolf/github-release.svg)]()
[![License](https://img.shields.io/github/license/maurobringolf/github-release.svg)]()
[![CircleCI branch](https://img.shields.io/circleci/project/github/maurobringolf/github-release/master.svg)]()

[Usage](#usage) | [Alternative solutions](#alternative-solutions)

*A bash script to draft a new GitHub release with an automatically generated changelog.*

Called inside a Git repository, this script generates a changelog based on commits from now back to the most recent tag and drafts a new tag and release via the GitHub API. It will directly open the edit page for the release in the browser, where it can be published, modified or discarded. **No tag or release will be published until you confirm it in the browser, the script simply prepares a draft for you.**

Commits can be grouped by type to create separate paragraphs in the changelog. This is done by prefixing the commit message with a type annotation, i.e.

    [internal] This is my commit message.

will be classified as internal change. The following types are supported:

* **breaking**
* **bugfix**
* **feature**
* **frontend**
* **backend**
* **workflow**
* **testing**
* **documentation**
* **internal**

The changelog by default lists them in this order. If you have more ideas for commit types, please file an issue or make a PR. There are plans for supporting custom types as command line argument [( #3 )]( https://github.com/maurobringolf/github-release/issues/3 ).

## Usage

This script should work with public repositories right away. For private repositories you need to provide a [GitHub API token](https://github.com/blog/1509-personal-api-tokens) because it creates the release using the GitHub releases API. For this script, the token should be put into an environment variable called `$AUTOMATIC_RELEASE_GITHUB_TOKEN` (If you think this is bad practice, tell me why and we can provide alternatives).

This is the complete list of options and flags, also available via `github-release -h`:

```
Usage:
  github-release --version
  github-release [-p]
  github-release [-h]

Options:
  --version Print version.
  -p        Show a preview of the changelog without releasing a new version.
  -h        Show this list describing usage and options.
```

## Alternative solutions

There is a range of tools solving the same problem as this one. The reason why I wrote my own is because *why not*. This is a pretty bad reason, so **you should probably consider using one of these instead:**

* [commitizen/cz-cli](https://github.com/commitizen/cz-cli)
* [conventional-changelog/conventional-github-releaser](https://github.com/conventional-changelog/conventional-github-releaser)
* [zeit/release](https://github.com/zeit/release)
* [skywinder/github-changelog-generator](https://github.com/skywinder/github-changelog-generator)

If, however you want *something to hack on*, use this one by all means! It is way simpler to understand and I will be happy to discuss problems and improvements.
