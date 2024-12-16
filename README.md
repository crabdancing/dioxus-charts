[![Discord Server](https://img.shields.io/discord/899851952891002890.svg?logo=discord&style=flat-square)](https://discord.gg/sKJSVNSCDJ)

# dioxus-charts 📊

A simple chart components library for [Dioxus](https://dioxuslabs.com/).

This crate provides some basic SVG-based chart components, customizable with
CSS, to be used with the Dioxus GUI library. The
components configuration was designed to be similar to what one would find
in JavaScript chart libraries.

The components available currently are:

- `PieChart`: for Pie, Donut and Gauge charts
- `BarChart`: for Bar and Stacked Bar charts, vertical or horizontal
- `LineChart`

You can check them out at the very simple [demo site](https://hiltonm.github.io/dioxus-charts-demo/)
for now.

## Usage

This crate is [on crates.io](https://crates.io/crates/dioxus-charts) and can be
used by adding `dioxus-charts` to your dependencies in your project's `Cargo.toml`.

```toml
[dependencies]
dioxus-charts = "0.3"
```

## Example

```rust
use dioxus::prelude::*;
use dioxus_charts::BarChart;

fn app() -> Element {
    rsx!(
        BarChart {
            padding_top: 30,
            padding_left: 70,
            padding_right: 50,
            padding_bottom: 30,
            bar_width: "10%",
            horizontal_bars: true,
            label_interpolation: (|v| format!("{v}%")) as fn(f32) -> String,
            series: vec![
                vec![63.0, 14.4, 8.0, 5.1, 1.8],
            ],
            labels: vec!["Chrome".into(), "Safari".into(), "IE/Edge".into(), "Firefox".into(), "Opera".into()]
        }
    )
}
 ```

There is also a couple of examples in the `examples` folder with a `Makefile.toml` that makes it easier
to build them. You need to install cargo-make first to make use of them:

```sh
cargo install cargo-make
```

You will also need to have [`sass`](https://sass-lang.com/) and [`tailwindcss`](https://tailwindcss.com/)
installed in your system for the make commands to generate the css files.

Then for the desktop demo, inside the examples folder:

```sh
cd examples
cargo make desktop
```

The web example was used to generate the [demo site](https://hiltonm.github.io/dioxus-charts-demo/).
To test it out yourself you need to have `trunk` for the dev-server and the rust wasm target installed:

```sh
cargo install trunk
rustup target add wasm32-unknown-unknown
```

Then build and launch the dev-server inside the examples folder:

```sh
cargo make web
```

Note: if you get hit by an error when the web example launches, its possible you were blessed by a version
mismatch issue caused by the rustwasm tooling getting out of sync. The simplest fix for that seems to be
to just remove the Cargo.lock file from the `examples/web` folder. Check
[this issue](https://github.com/rustwasm/wasm-bindgen/issues/2776) for more info if that doesn't do it.

Please check out the [Dioxus reference guide](https://dioxuslabs.com/learn/0.6/reference) for more
information.

## License

Licensed under either of [Apache License, Version 2.0](LICENSE-APACHE) or
[MIT License](LICENSE-MIT) at your option.

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in Dioxus-Charts by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
