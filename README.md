# github2gitea - Set up Gitea mirrors of GitHub repositories.

## Usage

All usage parameter can be set as command-line arguments:

```
usage: github2gitea [-h] [-c CONFIG_FILE] [-d] [-n] [-q] [--github-token GITHUB_TOKEN]
                    [--github-user GITHUB_USER] [--gitea-apiurl GITEA_APIURL]
                    [--gitea-token GITEA_TOKEN] [--mirror-forks]
                    [--mirror-owner MIRROR_OWNER] [--owner-filter OWNER_FILTER] [--recreate]
                    [--use-full-name]

Set up Gitea mirrors of GitHub repositories.

optional arguments:
  -h, --help            show this help message and exit
  -c CONFIG_FILE, --config-file CONFIG_FILE
                        path to config file
  -d, --debug           enable debug output
  -n, --dry-run         execute read-only actions
  -q, --quiet           enable quiet mode
  --github-token GITHUB_TOKEN
                        GitHub access token
  --github-user GITHUB_USER
                        GitHub user
  --gitea-apiurl GITEA_APIURL
                        Gitea API URL
  --gitea-token GITEA_TOKEN
                        Gitea access token
  --mirror-forks        mirror forks
  --mirror-owner MIRROR_OWNER
                        Gitea user or org owning the mirror repos
  --owner-filter OWNER_FILTER
                        GitHub repository owner filter
  --recreate            recreate mirrored repos if they already exist
  --use-full-name       use full repo name including owner
```

Alternatively, configuration parameters can be set in a json-formatted
file. Default search paths are
`$HOME/.config/github2gitea/config.json` and `$PWD/config.json`. An
additional file path can be added using the `-c/--config-file` option.
