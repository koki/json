# Koki's JSON library

It's a fork of `encoding/json` that annotates decoder errors with the path
(e.g. `$.pod.container.0.env`) where the error occurred.
The golang built-in implementation doesn't contextualize its errors, so it's hard to track down where they came from.

This library can also check for extraneous fields in your JSON, which is useful for detecting misspelled keys and other typos.

Also included in the `json/jsonutil` package: Additional utility functions for dealing with JSON
represented as `map[string]interface{}`, including an implementation of path-based indexing.

## How to use it

`github.com/koki/json` is a drop-in replacement for `encoding/json`. The decoder implementation is different, but the library API remains unchanged. Use this package's `json.Unmarshal` if you want paths for your decoder errors.

`github.com/koki/json/jsonutil` is a brand-new package. Use `jsonutil.ExtraneousFieldPaths` to get a list of paths that weren't decoded into your Go object. i.e. potential typos.

## Coming soon

Modified `json.Marshal` so the `omitempty` tag will omit zero-valued Go structs instead of encoding them as `{}`.
