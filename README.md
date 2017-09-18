# `github-release`

[![GitHub release](https://img.shields.io/github/release/maurobringolf/github-release.svg)]()
[![License](https://img.shields.io/github/license/maurobringolf/github-release.svg)]()
[![CircleCI branch](https://img.shields.io/circleci/project/github/maurobringolf/github-release/master.svg)]()

*A bash script to draft a new GitHub release with an automatically generated changelog.*

Called inside a Git repository, this script generates a changelog based on commits from now back to the most recent tag and drafts a new tag and release via the GitHub API. It will directly open the edit page for the release in the browser, where it can be published, modified or discarded.

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

The changelog by default lists them in this order. If you have more ideas for default types, please file an issue or make a PR. There are plans for adding more types as arguments ( https://github.com/maurobringolf/github-release/issues/3 ).

## Usage

This script should work with public repositories right away. For private repositories you need to provide a [GitHub API token](https://github.com/blog/1509-personal-api-tokens) because it creates the release using the GitHub releases API. For this script, the token should be put into an environment variable called `$AUTOMATIC_RELEASE_GITHUB_TOKEN`.
