# UMake Roadmap

## Version 0.1.0

### [JS] JavaScript Bundling

UMake should allow bundling regardless of the locally available
runtime (NodeJS, Deno or Bun).

The syntax should be as follows:

```bash
# Bundle a JavaScript project to commonjs
umake_js \
  --bundle \
  --input index.js \
  --target browser \
  --format commonjs \
  --outfile out.js
```

### [CORE] Parse Configuration

The core utility should be able to parse a `umake.toml` configuration
should read all necessary information from it and pass it into the
wrapper utility for a given language.

#### Example

For example, let's take following command:

```bash
umake target1
```

It is being executed in a directory that has a `umake.toml`
configuration with following contents:

```toml
[project]
name = 'example-project'

[targets.target1]
language = 'javascript'
action = 'bundle'

inputs = [
  'index.js'
]

target = 'browser'
format = 'commonjs'
outfile = 'out.js'
```

The program should now evaluate the configuration and pass the
extracted information to `umake_js` as arguments.

