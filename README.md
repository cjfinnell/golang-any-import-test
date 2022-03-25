# Golang `any` Import Test

With `any` introduced as a [predeclared identifier in golang1.18](https://tip.golang.org/ref/spec#Predeclared_identifiers), there's some ambiguity on whether importing a module that uses `any` into a project that uses golang version `<1.18`, this module was created to test that compatibility.
