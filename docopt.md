# docopt
# 命令行参数

## Example

```rust
#[macro_use]
extern crate serde_derive;
use docopt::Docopt;

// Write the Docopt usage string.
const USAGE: &'static str = "
Usage: cp [-a] <source> <dest>
       cp [-a] <source>... <dir>

Options:
    -a, --archive  Copy everything.
";

#[derive(Deserialize)]
struct Args {
    arg_source: Vec<String>,
    arg_dest: String,
    arg_dir: String,
    flag_archive: bool,
}

let argv = || vec!["cp", "-a", "file1", "file2", "dest/"];
let args: Args = Docopt::new(USAGE)
                        .and_then(|d| d.argv(argv().into_iter()).deserialize())
                        .unwrap_or_else(|e| e.exit());

// Now access your argv values.
fn s(x: &str) -> String { x.to_string() }
assert!(args.flag_archive);
assert_eq!(args.arg_source, vec![s("file1"), s("file2")]);
assert_eq!(args.arg_dir, s("dest/"));
assert_eq!(args.arg_dest, s(""));
```

docopt!

```rust
#![feature(plugin)]
#![plugin(docopt_macros)]

extern crate serde;

extern crate docopt;

// Write the Docopt usage string with the `docopt!` macro.
docopt!(Args, "
Usage: cp [-a] <source> <dest>
       cp [-a] <source>... <dir>

Options:
    -a, --archive  Copy everything.
")

fn main() {
    let argv = || vec!["cp", "-a", "file1", "file2", "dest/"];

    // Your `Args` struct has a single static method defined on it,
    // `docopt`, which will return a normal `Docopt` value.
    let args: Args = Args::docopt().deserialize().unwrap_or_else(|e| e.exit());

    // Now access your argv values.
    fn s(x: &str) -> String { x.to_string() }
    assert!(args.flag_archive);
    assert_eq!(args.arg_source, vec![s("file1"), s("file2")]);
    assert_eq!(args.arg_dir, s("dest/"));
    assert_eq!(args.arg_dest, s(""));
}
```
