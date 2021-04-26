# Deprecation notice

## How it works

1. Describe deprecation notice in a `go.mod`
```vgo
module github.com/kamilsk/platform

go 1.11

require (
	// ...
)

// Deprecated: the module is deprecated and no longer maintained;
// please use its alternatives.
//  - go.octolab.org
//  - go.octolab.org/toolkit/cli
//  - go.octolab.org/toolkit/protocol
```
2. Use `egg deps get` instead of the standard `go get` to see the notice
```bash
$ egg deps get github.com/kamilsk/platform
# go: finding github.com/kamilsk/platform v0.21.0
# go: downloading github.com/kamilsk/platform v0.21.0
# go: extracting github.com/kamilsk/platform v0.21.0
# go: deprecation github.com/kamilsk/platform
# 	the module is deprecated and no longer maintained;
# 	please use its alternatives.
# 	 - go.octolab.org
# 	 - go.octolab.org/toolkit/cli
# 	 - go.octolab.org/toolkit/protocol
```
