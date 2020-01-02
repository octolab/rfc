# Dependency patch

## How it works

1. Describe dependencies as usual
```vgo
module your.module

go 1.11

require (
	github.com/golang/mock v1.3.1
	github.com/golangci/golangci-lint v1.22.2
	github.com/kamilsk/egg v0.0.7
	golang.org/x/tools v0.2.2
)
```
2. Apply a known patch to them
```bash
$ egg deps patch --all
# Two patches were applied.
```
3. See a result
```vgo
module your.module

go 1.11

require (
	github.com/golang/mock v1.3.1
	github.com/golangci/golangci-lint v1.22.2
	github.com/kamilsk/egg v0.0.7
	golang.org/x/tools v0.2.2
)

replace github.com/izumin5210/gex => github.com/kamilsk/gex latest

replace golang.org/x/tools => github.com/kamilsk/go-tools latest
```
