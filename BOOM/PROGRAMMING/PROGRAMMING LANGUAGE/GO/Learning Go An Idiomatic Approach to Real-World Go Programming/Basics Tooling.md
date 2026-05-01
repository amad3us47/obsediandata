
Check the version of go
`go version`

run the go mod init command to mark this directory as a Go
module:
`go mod init hello_world`
go: creating new go.mod: module hello_world

The go.mod file declares the name of the module, the minimum supported version of
Go for the module, and any other modules that your module depends on. You can
think of it as being similar to the requirements.txt file used by Python or the Gemfile
used by Ruby.