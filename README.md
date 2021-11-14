![example workflow](https://github.com/glaslos/slicewriteseek/actions/workflows/go.yml/badge.svg)
[![GoDoc](https://godoc.org/github.com/glaslos/slicewriteseek?status.svg)](https://godoc.org/github.com/glaslos/slicewriteseek)
# SliceWriteSeek
SliceWriteSeeker implements WriteSeeker on a slice. There was a brief [discussion](https://github.com/golang/go/issues/21592) on adding such a feature to the stdlib.

### Sample Usage

```golang
s := slicewriteseek.New()
// write to it
if _, err := s.Write([]byte{1, 2, 3}); err != nil {
	panic(err)
}
// seek it
if off, err := s.Seek(0, io.SeekStart); err != nil || off != 0 {
	panic("Unexpected seek")
}
// read it
b := make([]byte, 1)
if _, err := s.Read(b); err != nil {
	panic(err)
}
```
