# xtrace-wannabe

A small Bash utility that prints a shell script in a format similar to `bash -x`
without actually executing it.

This project is mainly a learning experiment and is **not** a replacement for
Bash's real xtrace mode.

## Example

Input:

```bash
#!/bin/bash

name="Alice"

if [[ -f hello.txt ]]; then
    echo "Found!"
fi

echo "Done"
```

Output:

```text
+ name="Alice"
+ [[ -f hello.txt ]];
+ echo "Found!"
+ echo "Done"
```

## Features

- Does **not** execute the script.
- Produces output similar to `bash -x`.
- Ignores comments and blank lines.
- Lightweight and written entirely in Bash.

## Limitations

This is a static parser, not a Bash interpreter.

Because of that it cannot know:

- Which `if` branch would execute.
- How loops expand.
- Variable values.
- Command substitutions.
- Aliases.
- Functions.
- Shell expansions.
- Many Bash syntax edge cases.

In other words, the output is an approximation of what a script *looks like*,
not what Bash would actually execute.

## Usage

```bash
chmod +x static-xtracer
./static-xtracer script.sh
```
## License

MIT
