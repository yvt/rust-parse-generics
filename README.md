
# `parse-generics`

This repository contains several pieces related to the proposed [RFC #1583]:

- `parse-generics-poc` - a proof-of-concept implementation of the RFC.
- `parse-generics-shim` - a "polyfill" shim containing an implementation of a subset of the RFC in stable `macro_rules!`.
- `parse-macros` - a crate containing higher-level parsing macros built on top of `parse-generics-shim`.

A very basic example of using `parse-macros` in a crate, and then using *that* crate, is provided by the [`enum-as-str`](enum-as-str/) and [`enum-as-str-test`](enum-as-str-test/) crates.  Further examples can be found by looking at the `parse-macro` crate's `tests` directory.  Specifically:

- [`derive_clone.rs`](parse-macros/tests/derive_clone.rs) - a stable implementation of the built-in `Clone` derivation compiler plugin.
- [`derive_partial_ord.rs`](parse-macros/tests/derive_partial_ord.rs) - a stable implementation of the built-in `PartialOrd` derivation compiler plugin.  I was once *assured* this was impossible by a member of the core team.
- [`derive_serialize.rs`](parse-macros/tests/derive_serialize.rs) - a stable derivation macro for [`serde`]'s `Serialize` trait.  Does not support attributes (*e.g.* custom field names).
- [`reflect.rs`](parse-macros/tests/reflect.rs) - a *very* minimal compile-time reflection derivation macro.  Progress is blocked on not being able to define generic constants/statics, not on parsing or generation complexity.

**Links**

* Latest Releases ([`parse-generics-poc`](https://crates.io/crates/parse-generics-poc), [`parse-generics-shim`](https://crates.io/crates/parse-generics-shim), [`parse-macros`](https://crates.io/crates/parse-macros))
* Latest Docs ([`parse-generics-poc`](https://danielkeep.github.io/rust-parse-generics/doc/parse_generics_poc/index.html), [`parse-generics-shim`](https://danielkeep.github.io/rust-parse-generics/doc/parse_generics_shim/index.html), [`parse-macros`](https://danielkeep.github.io/rust-parse-generics/doc/parse_macros/index.html))
* [Repository](https://github.com/DanielKeep/rust-parse-generics)

## Supporting RFC #1583

The core team currently feels uneasy about accepting [RFC #1583], due to its complexity and the lack of demonstrable support for being able to correctly process generics and `where` clauses in macros.

If you would like to see it accepted, using the `parse-generics-shim` crate (and supporting its `use-parse-generics-poc` feature) will help demonstrate the desire for these macros to be accepted into the compiler.

[RFC #1583]: https://github.com/rust-lang/rfcs/pull/1583

## License

Licensed under either of

* MIT license (see [LICENSE](LICENSE) or <http://opensource.org/licenses/MIT>)
* Apache License, Version 2.0 (see [LICENSE](LICENSE) or <http://www.apache.org/licenses/LICENSE-2.0>)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you shall be dual licensed as above, without any additional terms or conditions.
