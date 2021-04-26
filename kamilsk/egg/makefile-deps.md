# Makefile dependencies

## How it works

1. Declare Makefile
```makefile
include src/common/env.mk
include src/go/env.mk
# ...
include src/go/tooling.mk
```
2. Some parts of it depend on each other
```makefile
PATHS       = $(shell go list ./... | sed -e "s|$(shell go list -m)/\{0,1\}||g")
# ...
VENDOR      = $(dir $(MODULE))
```
```makefile
.PHONY: format
format:
	@goimports -local $(VENDOR) -ungroup -w $(PATHS)
```
3. Declare dependencies between of them
```makefile
# require:
#  - env.mk
#  - ../some/other.mk

.PHONY: format
format:
	@goimports -local $(VENDOR) -ungroup -w $(PATHS)
```
4. Include only what you need
```makefile
include src/common/env.mk
include src/go/tooling.mk
```

## Notes

- Include only once.
- Use native syntax: `include ...`, instead of `# require:`.
