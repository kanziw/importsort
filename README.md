# importsort
> Inspired by https://github.com/aristanetworks/goarista/tree/master/cmd/importsort

## What's this?
It sorts golang imports into 3 groups like -
1. Standard packages
2. Third-party packages
3. your (e.g. `cvshub.com/company`) packages

```go
import (
	"bytes"
	"strings"

	"github.com/pkg/errors"

	a "cvshub.com/company/p"
	"cvshub.com/company/q"
)
```

## Install
```sh
go install github.com/kanziw/importsort@latest
```

## Usage
```
Usage of importsort:
  -l	list files whose formatting differs from importsort
  -s prefix
    	package prefix to define an import section, ex: "cvshub.com/company". May be specified multiple times. If not specified the repository root is used.
  -w	write result to file instead of stdout
```

#### Example
```sh
importsort -s github.com/kanziw -w main.go
```

### How to set in GoLand
1. Download [importsort.xml](./importsort.xml)
2. `Preferences` -> `Tools` -> `File Watchers` -> Import `importsort.xml`

### How to set in VSCode
1. Install [File Watcher](https://marketplace.visualstudio.com/items?itemName=appulate.filewatcher)
2. Edit setting.json
```json
  "filewatcher.commands": [
    {
      "match": "\\.go$",
      "isAsync": true,
      "cmd": "importsort -s cvshub.com/company -w ${file}",
      "event": "onFileChange"
    }
  ]
```
