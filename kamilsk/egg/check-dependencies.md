# Dependencies check

## How it works

1. Use `egg deps check license` to view license of your dependencies
```bash
$ egg deps check license
# +----------------------------+---------+
# | Module                     | License |
# +----------------------------+---------+
# | go.octolab.org             | MIT     |
# | go.octolab.org/toolkit/cli | MIT     |
# +----------------------------+---------+
```
2. Use `egg deps check version` to view version of your dependencies
```bash
$ egg deps check version
# +----------------------------+---------+--------+
# | Module                     | Version | Latest |
# +----------------------------+---------+--------+
# | go.octolab.org             | v0.0.6  | v0.0.8 |
# | go.octolab.org/toolkit/cli | v0.0.4  | v0.0.4 |
# +----------------------------+---------+--------+
```
