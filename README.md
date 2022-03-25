# Golang `any` Import Test

With `any` introduced as a [predeclared identifier in golang1.18](https://tip.golang.org/ref/spec#Predeclared_identifiers), there's some ambiguity on whether importing a module that uses `any` into a project that uses golang version `<1.18`, this module was created to test that compatibility.

It does `:(`
```
$ cat main.go 
package main

import importme "github.com/cjfinnell/golang-any-import-test"

type oldAnyer struct{}

func (oldAnyer) Any(x interface{}) interface{} {
        println("test")
        return nil
}

func main() {
        var a importme.Anyer = &oldAnyer{}
        a.Any("thing")
}
$ go run .   
# github.com/cjfinnell/golang-any-import-test
../../go/pkg/mod/github.com/cjfinnell/golang-any-import-test@v0.0.0-20220325143524-09ef142f72ba/interface.go:4:6: undefined: any
note: module requires Go 1.18
```
