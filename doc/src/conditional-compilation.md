# Conditional compilation

LALRPOP support conditional compilation of non-terminal declarations via
`#[cfg(feature = "FEATURE")]` attributes. If run in a build script LALRPOP will
automatically pickup the features from `cargo` and use those. Alternatively an
explicit set of features can be set using the `Configuration` type.

Like rust's `cfg` attribute, the syntax accepts `not()`, `any()` and `all()`
arguments, even nested.

```rust
#[cfg(feature = "FEATURE")]
pub MyRule1 : () = {
    ...
};

#[cfg(any(feature = "FEATURE_A", all(not(feature = "FEATURE_B"), feature = "FEATURE_C")))]
pub MyRule2 : () = {
    ...
};
```
