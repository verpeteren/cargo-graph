# cargo-graph

Linux: [![Build Status](https://travis-ci.org/kbknapp/cargo-graph.svg?branch=master)](https://travis-ci.org/kbknapp/cargo-graph)

A `cargo` subcommand for building GraphViz DOT files of dependency graphs. This subcommand was originally based off and inspired by the project [cargo-dot](https://github.com/maxsnew/cargo-dot) by [Max New](https://github.com/maxsnew)


## Demo

Let's say we wanted to build a dependency graph of [cargo-count](https://github.com/kbknapp/cargo-count) but we wanted optional dependencies to use red dashed lines and black boxes, and regular (aka "build") dependencies to use orange lines to green diamonds, one would run the following.

**NOTE:** GraphViz `dot` needs to be installed to produce the .PNG from the dotfile

```
$ cargo graph --optional-line-style dashed --optional-line-color red --optional-shape box --build-shape diamond --build-color green --build-line-color orange > cargo-count.dot
$ dot -Tpng > rainbow-graph.png cargo-count.dot
```

**NOTE:** It's also possible to run `cargo graph [options] | dot [options] > [file]` instead of individual commands

The first command produces a GraphViz DOT file which looks like this:

```
digraph dependencies {
	N0[label="cargo-count",shape=diamond,color=green, href="https://crates.io/crates/cargo-count"];
	N1[label="memchr",shape=diamond,color=green, href="https://crates.io/crates/memchr"];
	N2[label="ansi_term",shape=diamond,color=green, href="https://crates.io/crates/ansi_term"];
	N3[label="bitflags",shape=diamond,color=green, href="https://crates.io/crates/bitflags"];
	N4[label="aho-corasick",shape=diamond,color=green, href="https://crates.io/crates/aho-corasick"];
	N5[label="clap",shape=diamond,color=green, href="https://crates.io/crates/clap"];
	N6[label="clippy",shape=box, href="https://crates.io/crates/clippy"];
	N7[label="gitignore",shape=diamond,color=green, href="https://crates.io/crates/gitignore"];
	N8[label="glob",shape=diamond,color=green, href="https://crates.io/crates/glob"];
	N9[label="regex",shape=diamond,color=green, href="https://crates.io/crates/regex"];
	N10[label="tabwriter",shape=diamond,color=green, href="https://crates.io/crates/tabwriter"];
	N11[label="libc",shape=diamond,color=green, href="https://crates.io/crates/libc"];
	N12[label="strsim",shape=diamond,color=green, href="https://crates.io/crates/strsim"];
	N13[label="term_size",shape=diamond,color=green, href="https://crates.io/crates/term_size"];
	N14[label="unicode-segmentation",shape=diamond,color=green, href="https://crates.io/crates/unicode-segmentation"];
	N15[label="unicode-width",shape=diamond,color=green, href="https://crates.io/crates/unicode-width"];
	N16[label="vec_map",shape=diamond,color=green, href="https://crates.io/crates/vec_map"];
	N17[label="clippy_lints",shape=box, href="https://crates.io/crates/clippy_lints"];
	N18[label="matches",shape=box, href="https://crates.io/crates/matches"];
	N19[label="quine-mc_cluskey",shape=box, href="https://crates.io/crates/quine-mc_cluskey"];
	N20[label="regex-syntax",shape=diamond,color=green, href="https://crates.io/crates/regex-syntax"];
	N21[label="rustc-serialize",shape=box, href="https://crates.io/crates/rustc-serialize"];
	N22[label="semver",shape=box, href="https://crates.io/crates/semver"];
	N23[label="toml",shape=box, href="https://crates.io/crates/toml"];
	N24[label="unicode-normalization",shape=box, href="https://crates.io/crates/unicode-normalization"];
	N25[label="kernel32-sys",shape=diamond,color=green, href="https://crates.io/crates/kernel32-sys"];
	N26[label="winapi",shape=diamond,color=green, href="https://crates.io/crates/winapi"];
	N27[label="winapi-build",shape=diamond,color=green, href="https://crates.io/crates/winapi-build"];
	N28[label="nom",shape=box, href="https://crates.io/crates/nom"];
	N29[label="thread_local",shape=diamond,color=green, href="https://crates.io/crates/thread_local"];
	N30[label="utf8-ranges",shape=diamond,color=green, href="https://crates.io/crates/utf8-ranges"];
	N31[label="thread-id",shape=diamond,color=green, href="https://crates.io/crates/thread-id"];
	N0 -> N2[label="",color=orange];
	N0 -> N5[label="",color=orange];
	N0 -> N6[label="",style=dashed,color=red];
	N0 -> N7[label="",color=orange];
	N0 -> N8[label="",color=orange];
	N0 -> N9[label="",color=orange];
	N0 -> N10[label="",color=orange];
	N1 -> N11[label="",color=orange];
	N4 -> N1[label="",color=orange];
	N5 -> N2[label="",color=orange];
	N5 -> N3[label="",color=orange];
	N5 -> N11[label="",color=orange];
	N5 -> N12[label="",color=orange];
	N5 -> N13[label="",color=orange];
	N5 -> N14[label="",color=orange];
	N5 -> N15[label="",color=orange];
	N5 -> N16[label="",color=orange];
	N6 -> N17[label="",style=dashed,color=red];
	N7 -> N8[label="",color=orange];
	N9 -> N1[label="",color=orange];
	N9 -> N4[label="",color=orange];
	N9 -> N20[label="",color=orange];
	N9 -> N29[label="",color=orange];
	N9 -> N30[label="",color=orange];
	N10 -> N15[label="",color=orange];
	N13 -> N11[label="",color=orange];
	N13 -> N25[label="",color=orange];
	N13 -> N26[label="",color=orange];
	N17 -> N18[label="",style=dashed,color=red];
	N17 -> N19[label="",style=dashed,color=red];
	N17 -> N20[label="",style=dashed,color=red];
	N17 -> N21[label="",style=dashed,color=red];
	N17 -> N22[label="",style=dashed,color=red];
	N17 -> N23[label="",style=dashed,color=red];
	N17 -> N24[label="",style=dashed,color=red];
	N22 -> N28[label="",style=dashed,color=red];
	N23 -> N21[label="",style=dashed,color=red];
	N25 -> N26[label="",color=orange];
	N25 -> N27[label="",color=orange];
	N29 -> N31[label="",color=orange];
	N31 -> N11[label="",color=orange];
	N31 -> N25[label="",color=orange];
}
```

The second command produces a PNG image of the graph which looks like:

![cargo-count dependencies](rainbow-graph.png)

Now, *why* someone would do that to a graph is a different story...but it's possible :)

## Installing

`cargo-graph` can be installed with `cargo install`

```
$ cargo install cargo-graph
```

This may require a nightly version of `cargo` if you get an error about the `install` command not being found. You may also compile and install the traditional way by following the instructions below.


## Compiling

Follow these instructions to compile `cargo-count`, then skip down to Installation.

 1. Ensure you have current version of `cargo` and [Rust](https://www.rust-lang.org) installed
 2. Clone the project `$ git clone https://github.com/kbknapp/cargo-graph && cd cargo-graph`
 3. Build the project `$ cargo build --release` (**NOTE:** There is a large performance difference when compiling without optimizations, so I recommend always using `--release` to enable to them)
 4. Once complete, the binary will be located at `target/release/cargo-graph`

## Installation and Usage

All you need to do is place `cargo-graph` somewhere in your `$PATH`. Then run `cargo graph` anywhere in your project directory. For full details see below.

### Linux / OS X

You have two options, place `cargo-graph` into a directory that is already located in your `$PATH` variable (To see which directories those are, open a terminal and type `echo "${PATH//:/\n}"`, the quotation marks are important), or you can add a custom directory to your `$PATH`

**Option 1**
If you have write permission to a directory listed in your `$PATH` or you have root permission (or via `sudo`), simply copy the `cargo-graph` to that directory `# sudo cp cargo-graph/usr/local/bin`

**Option 2**
If you do not have root, `sudo`, or write permission to any directory already in `$PATH` you can create a directory inside your home directory, and add that. Many people use `$HOME/.bin` to keep it hidden (and not clutter your home directory), or `$HOME/bin` if you want it to be always visible. Here is an example to make the directory, add it to `$PATH`, and copy `cargo-graph` there.

Simply change `bin` to whatever you'd like to name the directory, and `.bashrc` to whatever your shell startup file is (usually `.bashrc`, `.bash_profile`, or `.zshrc`)

```sh
$ mkdir ~/bin
$ echo "export PATH=$PATH:$HOME/bin" >> ~/.bashrc
$ cp cargo-graph~/bin
$ source ~/.bashrc
```

### Windows

On Windows 7/8 you can add directory to the `PATH` variable by opening a command line as an administrator and running

```sh
C:\> setx path "%path%;C:\path\to\cargo-graph\binary"
```

Otherwise, ensure you have the `cargo-graph` binary in the directory which you operating in the command line from, because Windows automatically adds your current directory to PATH (i.e. if you open a command line to `C:\my_project\` to use `cargo-graph` ensure `cargo-graph.exe` is inside that directory as well).


### Options

There are a few options for using `cargo-graph` which should be somewhat self explanatory.

```
USAGE:
    cargo graph [FLAGS] [OPTIONS]

FLAGS:
    -h, --help       Prints help information
    -I, --include-versions    Include the dependency version on nodes
    -V, --version    Prints version information

OPTIONS:
        --build-color <COLOR>            Color for regular deps (Defaults to 'black')
                                          [values: blue black yellow purple green red white orange]
        --build-deps <true|false>        Should build deps be in the graph? (Defaults to 'true')
                                         ex. --build-deps=false OR --build-deps=no
        --build-line-color <COLOR>       Line color for regular deps (Defaults to 'black')
                                          [values: blue black yellow purple green red white orange]
        --build-line-style <STYLE>       Line style for build deps (Defaults to 'solid')
                                          [values: solid dotted dashed]
        --build-shape <SHAPE>            Shape for regular deps (Defaults to 'round')
                                          [values: box round diamond triangle]
        --dev-color <COLOR>              Color for dev deps (Defaults to 'black')
                                          [values: blue black yellow purple green red white orange]
        --dev-deps <true|false>          Should dev deps be included in the graph? (Defaults to 'false')
                                         ex. --dev-deps=true OR --dev-deps=yes
        --dev-line-color <COLOR>         Line color for dev deps (Defaults to 'black')
                                          [values: blue black yellow purple green red white orange]
        --dev-line-style <STYLE>         Line style for dev deps (Defaults to 'solid')
                                          [values: solid dotted dashed]
        --dev-shape <SHAPE>              Shape for dev deps (Defaults to 'round')
                                          [values: box round diamond triangle]
        --dot-file <FILE>                Output file (Default to stdout)
        --lock-file <FILE>               Specify location of .lock file (Default 'Cargo.lock')
        --manifest-file <FILE>           Specify location of manifest file (Default 'Cargo.toml')
        --optional-color <COLOR>         Color for optional deps (Defaults to 'black')
                                          [values: blue black yellow purple green red white orange]
        --optional-deps <true|false>     Should optional deps be in the graph? (Defaults to 'true')
                                         ex. --optional-deps=false OR --optional-deps=no
        --optional-line-color <COLOR>    Line color for optional deps (Defaults to 'black')
                                          [values: blue black yellow purple green red white orange]
        --optional-line-style <STYLE>    Line style for optional deps (Defaults to 'solid')
                                          [values: solid dotted dashed]
        --optional-shape <SHAPE>         Shape for optional deps (Defaults to 'round')
                                          [values: box round diamond triangle]
```

## License

`cargo-graph` is released under the terms of the MIT. See the LICENSE-MIT file for the details.

## Dependencies Tree
![cargo-graph dependencies](cargo-graph.png)
