# xmlem

XML DOM manipulation for Rust.

## Quickstart

```rust
let mut doc = Document::from_str("<root><potato /></root>").unwrap();
let root = doc.root();

let potato = root.query_selector(&doc, Selector::new("potato").unwrap()).unwrap();
potato.append_new_element(&mut doc, (
    "wow",
    [
        ("easy", "true"),
        ("x", "200"),
    ],
));
    
let decl = Declaration {
    version: Some("1.1".to_string()),
    encoding: Some("utf-8".to_string()),
    standalone: None,
}
doc.set_declaration(Some(decl));

println!("{}", doc.to_string_pretty());

/*
Prints:

<?xml version="1.1" encoding="utf-8" ?>
<root>
  <potato>
    <wow easy="true" x="200" />
  </potato>
</root>
*/
```

You can run this example with `cargo run --example readme`, and see the `examples/readme.rs` file.

## License

This project is licensed under either of

 * Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.