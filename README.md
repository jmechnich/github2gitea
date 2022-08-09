[![PyPI versio](https://img.shields.io/pypi/v/github2gitea)](https://pypi.org/project/github2gitea/)
[![PyPi format](https://img.shields.io/pypi/format/github2gitea)](https://pypi.org/project/github2gitea/)
[![PyPI license](https://img.shields.io/pypi/l/github2gitea)](https://pypi.org/project/github2gitea/)
[![PyPi weekly downloads](https://img.shields.io/pypi/dw/github2gitea)](https://pypi.org/project/github2gitea/)

## github2gitea

Migrates GitHub repositories to Gitea.

`github2gitea` is a command-line application for importing and
mirroring GitHub repositories to Gitea. It can be used as well for
continously adding newly created repositories in regular intervals,
e.g. using cron.

### Usage

All usage parameter can be set as command-line arguments:

```
usage: github2gitea [-h] [-c CONFIG_FILE] [-d] [-n] [-p] [-q] [-s]
                    [--github-token GITHUB_TOKEN] [--github-user GITHUB_USER]
                    [--gitea-apiurl GITEA_APIURL] [--gitea-token GITEA_TOKEN]
                    [--migrate-forks] [--owner-filter OWNER_FILTER] [--migrate-issues]
                    [--migrate-labels] [--migrate-milestones] [--migrate-pull-requests]
                    [--migrate-releases] [--migrate-wikis] [--mirror]
                    [--mirror-interval MIRROR_INTERVAL] [--owner OWNER] [--recreate]
                    [--use-full-name]
                    [repos ...]

Migrate GitHub repositories to Gitea.

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
  -s, --syslog          enable logging to syslog
  --github-token GITHUB_TOKEN
                        set GitHub access token
  --github-user GITHUB_USER
                        set GitHub user
  --gitea-apiurl GITEA_APIURL
                        set Gitea API URL
  --gitea-token GITEA_TOKEN
                        set Gitea access token
  --migrate-forks       migrate forks
  --owner-filter OWNER_FILTER
                        set GitHub repository owner filter
  --migrate-issues      migrate issues
  --migrate-labels      migrate labels
  --migrate-milestones  migrate milestones
  --migrate-pull-requests
                        migrate pull requests (not yet fully implemented in Gitea)
  --migrate-releases    migrate releases (not yet fully implemented in Gitea)
  --migrate-wikis       migrate wikis
  --mirror              set up mirroring of repo
  --mirror-interval MIRROR_INTERVAL
                        mirror interval (default: 8 hours). Valid time units are "h", "m,
                        "s". 0 to disable automatic sync
  --owner OWNER         set Gitea user or org owning the repos (default: owner of used access
                        token)
  --recreate            recreate repos if they already exist
  --use-full-name       use full repo name including owner for migration (i.e. "owner_name")
```

Alternatively, configuration parameters can be set in a json-formatted
file.

Default search paths are:
* `$HOME/.config/github2gitea/config.json`
* `$PWD/config.json`

An additional file path can be added using the `-c/--config-file`
option.

### Minimal settings required for running

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
