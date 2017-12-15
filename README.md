# Koki's JSON library

It's a fork of `encoding/json` that annotates decoder errors with the path
(e.g. `$.pod.container.0.env`) where the error occurred.
The golang built-in implementation doesn't contextualize its errors, so it's hard to track down where they came from.

This library can also check for extraneous fields in your JSON, which is useful for detecting misspelled keys and other typos.

Also included in the `json/jsonutil` package: Additional utility functions for dealing with JSON
represented as `map[string]interface{}`, including an implementation of path-based indexing.
