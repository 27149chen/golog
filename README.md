# golog

[![Travis CI](https://img.shields.io/travis/bingoohuang/golog/master.svg?style=flat-square)](https://travis-ci.com/bingoohuang/golog)
[![Software License](https://img.shields.io/badge/License-MIT-orange.svg?style=flat-square)](https://github.com/bingoohuang/golog/blob/master/LICENSE.md)
[![GoDoc](https://img.shields.io/badge/godoc-reference-blue.svg?style=flat-square)](https://godoc.org/github.com/bingoohuang/golog)
[![Coverage Status](http://codecov.io/github/bingoohuang/golog/coverage.svg?branch=master)](http://codecov.io/github/bingoohuang/golog?branch=master)
[![goreport](https://www.goreportcard.com/badge/github.com/bingoohuang/golog)](https://www.goreportcard.com/report/github.com/bingoohuang/golog)

golog

## Integration with logrus

```go
func init() {
    golog.SetupLogrus(nil, "level=debug,rotate=.yyyy-mm-dd-HH-mm-ss,maxAge=5s,gzipAge=3s")
}
```

specifications available

name | default value | description
---  | ---           | ---
level| info          | log level to record (debug/info/warn/error)
file | ~/logs/{bin}.log | base log file
rotate| .yyyy-MM-dd  | time rotate pattern(yyyy-MM-dd HH:mm:ss.SSS)
maxAge| 30d          | max age to keep log files (unit s/m/h/d/w)
gzipAge| 3d          | gzip aged log files 
maxSize| 100M        | max size to rotate log files (unit K/M/K)
printColor| true     | print color on the log level or not
printCall | true     | print caller file and line number  or not (performance slow)
stdout   | true      | print the log to stdout at the same time or not

## Demonstration

```bash
$ go get github.com/bingoohuang/golog/gologdemo
$ ADDR=":54264" gologdemo
start to listen on :54264
log file created: gologdemo.log
2020-07-17 17:01:42.968    INFO 7002 --- [   19] [-]           main.go:34 : {"contemtType":"","proto":"HTTP/1.1"} [::1]:56946 GET /abc
2020-07-17 17:01:45.974    INFO 7002 --- [   34] [-]           main.go:34 : {"contemtType":"","proto":"HTTP/1.1"} [::1]:56958 GET /abc
2020-07-17 17:01:46.977    INFO 7002 --- [   21] [-]           main.go:34 : {"contemtType":"","proto":"HTTP/1.1"} [::1]:56963 GET /abc
2020-07-17 17:01:47.900    INFO 7002 --- [    5] [-]           main.go:34 : {"contemtType":"","proto":"HTTP/1.1"} [::1]:56968 GET /abc
```

