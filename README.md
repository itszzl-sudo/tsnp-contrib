# tsnp-contrib - Official Plugins for ts-native

Official plugin implementations for the [ts-native](https://github.com/itszzl-sudo/ts-native) TypeScript to native compiler.

## Available Plugins

| Plugin | Description | Platforms |
|--------|-------------|-----------|
| [http](http/) | HTTP client for making web requests | Windows, Linux, macOS |
| [fs](fs/) | File system operations (read, write, delete) | Windows, Linux, macOS |
| [crypto](crypto/) | Cryptographic functions (SHA256, MD5, etc.) | Windows, Linux, macOS |
| [os](os/) | Operating system information | Windows, Linux, macOS |
| [path](path/) | Path manipulation utilities | Windows, Linux, macOS |
| [cli](cli/) | Command-line argument parsing | Windows, Linux, macOS |
| [timer](timer/) | Timer and scheduling functions | Windows, Linux, macOS |
| [json](json/) | JSON parsing and serialization | Windows, Linux, macOS |
| [net](net/) | Network socket operations | Windows, Linux, macOS |
| [process](process/) | Process management and control | Windows, Linux, macOS |
| [log](log/) | Logging framework | Windows, Linux, macOS |
| [env](env/) | Environment variable access | Windows, Linux, macOS |

## Usage

### As Git Submodule

These plugins are included in [cargo-tsn](https://github.com/itszzl-sudo/cargo-tsn) as a Git submodule:

```bash
# Clone cargo-tsn with submodule
git clone --recurse-submodules https://github.com/itszzl-sudo/cargo-tsn.git
cd cargo-tsn

# Copy plugins to your project
cp -r tsnp-contrib/http your-project/tsnp/
cp -r tsnp-contrib/fs your-project/tsnp/
```

### Manual Installation

1. Clone this repository:
```bash
git clone https://github.com/itszzl-sudo/tsnp-contrib.git
```

2. Copy desired plugins to your ts-native project:
```bash
cd your-project
cp -r /path/to/tsnp-contrib/http tsnp/
cp -r /path/to/tsnp-contrib/fs tsnp/
```

3. Compile your TypeScript code:
```bash
ts-native main.ts
./main.exe
```

## Plugin Structure

Each plugin follows a standard structure:

```
<plugin>/
├── <plugin>_win.c        # Windows implementation
├── <plugin>_linux.c      # Linux implementation
├── <plugin>_macos.c      # macOS implementation
├── ts-native.toml        # Main configuration
├── ts-native-win.toml    # Windows platform config
├── ts-native-linux.toml  # Linux platform config
├── ts-native-macos.toml  # macOS platform config
└── index.d.ts            # TypeScript declarations
```

## Plugin Priority

Official plugins have priority `0` by default. Custom plugins created with `cargo tsn prepare` have priority `1000`, so custom plugins always take precedence over official ones.

## Development

### Adding a New Plugin

1. Create plugin directory:
```bash
mkdir -p my-plugin
```

2. Create platform implementations:
- `my-plugin_win.c`
- `my-plugin_linux.c`
- `my-plugin_macos.c`

3. Create configuration files:
- `ts-native.toml`
- `ts-native-win.toml`
- `ts-native-linux.toml`
- `ts-native-macos.toml`

4. Add TypeScript declarations:
- `index.d.ts`

5. Test with ts-native compiler

### Testing

Each plugin should be tested on all supported platforms:

```bash
# Windows
ts-native test.ts
./test.exe

# Linux
ts-native test.ts
./test

# macOS
ts-native test.ts
./test
```

## License

MIT

## Related Projects

- [ts-native](https://github.com/itszzl-sudo/ts-native) - TypeScript to native compiler
- [cargo-tsn](https://github.com/itszzl-sudo/cargo-tsn) - Project management tool
