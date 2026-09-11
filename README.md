# disasmdb

[![Annotations](https://img.shields.io/github/directory-file-count/retroenv/disasmdb?type=file&extension=ini&label=annotations)](https://github.com/retroenv/disasmdb)
[![For retrodisasm](https://img.shields.io/badge/for-retrodisasm-6f42c1)](https://github.com/retroenv/retrodisasm)
[![License: CC0-1.0](https://img.shields.io/github/license/retroenv/disasmdb)](LICENSE)

Community-maintained ROM annotations for [retrodisasm](https://github.com/retroenv/retrodisasm)
across classic game systems. Annotation files provide names, comments, and
code/data boundaries for generating readable disassemblies from your own ROMs.

## Benefits

- Share disassembly knowledge without distributing ROMs or game code: annotations
  describe the ROM, while users supply its bytes locally.
- Generate assembly that reassembles byte-for-byte to the original ROM. Use
  `-verify` with a supported installed assembler to check the match.
- Reuse the same annotations across assembler formats. For NES, retrodisasm
  supports ca65, asm6, NESASM, and retroasm output via `-a`.

## Layout

Files are grouped by console and then the first letter of the game title:

```text
nes/
  s/
    sample-game-world.ini
```

Use lowercase console folders and title initials (`a`–`z`, or `0-9` for digits).
Keep leading articles such as “The”. Use kebab-case filenames, adding region
and revision where needed.

## Usage

Use a retrodisasm version that supports `-annotations`. From this repository:

```sh
retrodisasm -annotations "<console>/<initial>/<game>.ini" -a ca65 -o game.asm game.nes
```

Replace the annotation path and ROM filename with your game's files.
retrodisasm rejects ROMs that do not match the annotation's checksums.

See the [annotation format documentation](https://github.com/retroenv/retrodisasm/blob/main/docs/annotations.md)
for supported sections and expressions.

## Contributing

- Follow the console/title layout and identify the supported region and revision.
- Include ROM checksums and preserve source attribution in the annotation file.
- Validate annotations with a matching ROM and inspect the generated output.
- Keep ROMs, generated assemblies, and build artifacts outside this repository.

## License

Original contributions are provided under [CC0 1.0 Universal](LICENSE).
Third-party material retains its applicable rights; this dedication does not
relicense the referenced games or upstream sources.

Sharing annotations does not automatically eliminate copyright concerns. Use
original comments and material you have permission to share. Under
[U.S. copyright guidance](https://www.copyright.gov/help/faq/faq-protect.html),
facts are not protected, but their creative expression may be.
