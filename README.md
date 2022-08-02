[![PyPI versio](https://img.shields.io/pypi/v/github2gitea)](https://pypi.org/project/github2gitea/)
[![PyPi format](https://img.shields.io/pypi/format/github2gitea)](https://pypi.org/project/github2gitea/)
[![PyPI license](https://img.shields.io/pypi/l/github2gitea)](https://pypi.org/project/github2gitea/)
[![PyPi weekly downloads](https://img.shields.io/pypi/dw/github2gitea)](https://pypi.org/project/github2gitea/)

# github2gitea - Set up Gitea mirrors of GitHub repositories

`github2gitea` is a command-line application for setting up Gitea
mirrors of GitHub repositories. It can be used as well for continously
adding new mirrors in regular intervals, e.g. using cron.

## Usage

All usage parameter can be set as command-line arguments:

```
usage: github2gitea [-h] [-c CONFIG_FILE] [-d] [-n] [-p] [-q] [--github-token GITHUB_TOKEN]
                    [--github-user GITHUB_USER] [--gitea-apiurl GITEA_APIURL]
                    [--gitea-token GITEA_TOKEN] [--mirror-forks]
                    [--owner-filter OWNER_FILTER] [--mirror-interval MIRROR_INTERVAL]
                    [--mirror-issues] [--mirror-labels] [--mirror-milestones]
                    [--mirror-owner MIRROR_OWNER] [--mirror-pull-requests]
                    [--mirror-releases] [--mirror-wikis] [--recreate] [--use-full-name]
                    [repos ...]

Set up Gitea mirrors of GitHub repositories.

positional arguments:
  repos                 (optional) explicit list of GitHub repositories formatted as
                        owner/name

optional arguments:
  -h, --help            show this help message and exit
  -c CONFIG_FILE, --config-file CONFIG_FILE
                        path to config file
  -d, --debug           enable debug output
  -n, --dry-run         execute read-only actions
  -p, --print-config    print configuration and exit
  -q, --quiet           enable quiet mode
  --github-token GITHUB_TOKEN
                        set GitHub access token
  --github-user GITHUB_USER
                        set GitHub user
  --gitea-apiurl GITEA_APIURL
                        set Gitea API URL
  --gitea-token GITEA_TOKEN
                        set Gitea access token
  --mirror-forks        mirror forks
  --owner-filter OWNER_FILTER
                        set GitHub repository owner filter
  --mirror-interval MIRROR_INTERVAL
                        mirror interval (default: 8 hours). Valid time units are "h", "m,
                        "s". 0 to disable automatic sync.
  --mirror-issues       mirror issues (not yet fully implemented in Gitea)
  --mirror-labels       mirror labels (not yet fully implemented in Gitea)
  --mirror-milestones   mirror milestones (not yet fully implemented in Gitea)
  --mirror-owner MIRROR_OWNER
                        set Gitea user or org owning the mirror repos (default: owner of used
                        access token)
  --mirror-pull-requests
                        mirror pull requests (not yet fully implemented in Gitea)
  --mirror-releases     mirror releases (not yet fully implemented in Gitea)
  --mirror-wikis        mirror wikis
  --recreate            recreate mirrored repos if they already exist
  --use-full-name       use full repo name including owner for mirror (i.e. "owner_name")
```

Alternatively, configuration parameters can be set in a json-formatted
file.

Default search paths are:
* `$HOME/.config/github2gitea/config.json`
* `$PWD/config.json`

An additional file path can be added using the `-c/--config-file`
option.

## Minimal settings required for running

First, create a Personal Access Token on GitHub with at least scope
`repo`. Consider setting an unlimited lifetime.

Create a Gitea access token for your user.

Set the following in a configuration file (or the corresponding
command-line options):

```
{
  "github_user"  : "GITHUB_USERNAME",
  "github_token" : "GITHUB_PERSONAL_ACCESS_TOKEN",
  "gitea_apiurl" : "GITEA_APIURL",
  "gitea_token"  : "GITEA_ACCESS_TOKEN"
}
```
