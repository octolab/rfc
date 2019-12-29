# Mirror support

## How it works

1. Create mirror upstream
```bash
$ git remote -v
# mirror	git@bitbucket.org:octolab/pkg.git (fetch)
# mirror	git@bitbucket.org:octolab/pkg.git (push)
# origin	git@github.com:octolab/pkg.git (fetch)
# origin	git@github.com:octolab/pkg.git (push)
```
2. Use `egg vanity generate html`
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta name="go-import" content="go.octolab.org git https://github.com/octolab/pkg">
        <meta name="go-source" content="go.octolab.org https://github.com/octolab/pkg https://github.com/octolab/pkg/blob/master{/dir} https://github.com/octolab/pkg/blob/master{/dir}/{file}#L{line}">
        <meta name="go-import" content="go.octolab.org git https://bitbucket.org/octolab/pkg" is="mirror">
        <meta name="go-source" content="go.octolab.org https://bitbucket.org/octolab/pkg https://bitbucket.org/octolab/pkg/src/master{/dir} https://bitbucket.org/octolab/pkg/src/master{/dir}/{file}#L{line}" is="mirror">
        <meta http-equiv="content-type" content="text/html; charset=utf-8">
        <meta http-equiv="refresh" content="0; url=https://godoc.org/go.octolab.org">
        <title>go.octolab.org</title>
    </head>
    <body>
        Nothing to see here. Please <a href="https://godoc.org/go.octolab.org">move along</a>.
    </body>
</html>
```
3. Or `egg vanity generate yaml`
```yaml
- prefix: go.octolab.org
  import:
    - url: https://github.com/octolab/pkg
      vcs: git
      source: 
        url: '{{.Import.URL}}'
        dir: '{{.URL}}/blob/master{/dir}'
        file: '{{.Dir}}/{file}#L{line}'
    - url: https://bitbucket.org/octolab/pkg
      vcs: git
      is: mirror
      source:
        url: '{{.Import.URL}}'
        dir: '{{.URL}}/src/master{/dir}'
        file: '{{.Dir}}/{file}#L{line}'
```
4. Use `egg deps get` instead of the standard `go get`
```bash
$ egg deps get go.octolab.org
# go: finding go.octolab.org v0.0.7
# go: cannot fetch from github, fallback to bitbucket
# go: downloading go.octolab.org v0.0.7
# go: extracting go.octolab.org v0.0.7
```
