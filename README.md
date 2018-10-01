# test-gocode

Looking into an issue with `gocode-gomod` so I created this repo.

Clone it outside your `GOPATH` and build it, then to reproduce try and import one of the go stdlib packages.

With a new clean vscode editor I ran.

```
$ gocode-gomod close
$ gocode-gomod -s -debug
```

And completion was not functioning for stdlib packages.

```
package main
import "encoding/base64"

import "github.com/sirupsen/logrus"

func main() {
	logrus.Printf("logging")

	base64.#
}
2018/10/02 06:17:49 -------------------------------------------------------
go list stderr <<# main.go
./main.go:8:2: undefined: base64
>>
2018/10/02 06:17:49 Elapsed duration: 168.943019ms
2018/10/02 06:17:49 Offset: 0
2018/10/02 06:17:49 Number of candidates found: 0
2018/10/02 06:17:49 Candidates are:
2018/10/02 06:17:49 =======================================================
```

See https://github.com/Microsoft/vscode-go/issues/1939