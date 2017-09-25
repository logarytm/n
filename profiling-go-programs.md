# Profiling Go programs — the top of the iceberg

Add the following code to generate a CPU profile:

```go
import (
  "runtime/pprof"
)

func main() {
  var cpuprofile = flag.String("cpuprofile", "", "write cpu profile to file")
  flag.Parse()

  if *cpuprofile != "" {
    prof, err := os.Create()
    if err != nil {
      panic(err)
    }
    pprof.StartCPUProfile(prof)
    defer pprof.StopCPUProfile()
  }
}
```

Run your program with `-cpuprofile=<file>`:

```
go build foo.go
./foo -cpuprofile=foo.prof
```

Load your profile in `pprof`:

```
go tool pprof foo foo.prof
```

Then use `kcachegrind` to display the profile in
[KCacheGrind](http://kcachegrind.sourceforge.net/html/Home.html), or (provided
you have installed GraphViz and have `dot` in your PATH) `png` to generate
a PNG graph. Or call for `help` to list all commands.

## Linkography

- https://blog.golang.org/profiling-go-programs
