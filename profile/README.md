<div align="center">

# BTOON

**MessagePack, with tables that store each key once.**

[Website](https://btoon.net) · [Playground](https://btoon.net/docs#playground) · [Specification](https://github.com/BTOON-project/btoon-core/blob/main/docs/SPEC.md) · [Benchmarks](https://btoon.net/benchmarks)

</div>

BTOON ("Binary TOON") is a compact binary serialization format. It is MessagePack plus
a columnar encoding for arrays of records that share their keys. That's the idea behind
[TOON](https://github.com/toon-format/toon), in binary form, for storage and transport
between programs.

- **Smaller for record-shaped data.** Each key of a table is written once, followed by
  each column's values. 10,000 user records take 447 KB, against 767 KB as
  MessagePack and 1,018 KB as JSON.
- **Valid MessagePack.** BTOON's own types are negative extension ids, so any
  MessagePack decoder can still read a document. BTOON decoders read MessagePack whose
  map keys are strings.
- **Canonical.** A value has exactly one encoding. Every library writes the same bytes,
  checked against 260 shared conformance vectors.
- **Extension types:** timestamps with nanoseconds and a UTC offset, dates,
  arbitrary-precision integers, and float32/float64 vectors for embeddings.
- **Optional envelopes:** compression (zlib in every library, plus LZ4, Zstandard, Brotli
  and Snappy where available) and HMAC-SHA256 signatures.
- **Safe on hostile input.** Decoders bounds-check every read, limit nesting and
  decompressed size, validate UTF-8, and are fuzzed.

## Libraries

| Language | Repository | Package | Notes |
|---|---|---|---|
| C++ | [btoon-core](https://github.com/BTOON-project/btoon-core) | build from source | Reference implementation, the spec, the conformance vectors and the `btoon` CLI |
| Python | [btoon-python](https://github.com/BTOON-project/btoon-python) | `btoon` (PyPI) | Native extension over btoon-core |
| Node.js | [btoon-nodejs](https://github.com/BTOON-project/btoon-nodejs) | `btoon` (npm) | Node-API addon over btoon-core |
| JavaScript / TypeScript | [btoon-javascript](https://github.com/BTOON-project/btoon-javascript) | `@btoon/js` (npm) | Pure TypeScript, no dependencies: browsers, Node.js, Deno, Bun, edge runtimes |
| Go | [btoon-go](https://github.com/BTOON-project/btoon-go) | `github.com/BTOON-project/btoon-go` | Pure Go, no cgo |
| PHP | [btoon-php](https://github.com/BTOON-project/btoon-php) | `btoon/btoon` (Packagist) | Pure PHP 8.2+ |
| Website | [btoon-web](https://github.com/BTOON-project/btoon-web) | [btoon.net](https://btoon.net) | Docs, in-browser playground, benchmarks |

Every library implements spec 0.1 at version 0.1.0. **0.1.0 isn't published to the
package registries yet.** PyPI (`btoon` 0.0.1) and npm (`btoon` 0.0.7) still have the
older 0.0.x releases, whose format is not compatible. Until the release, each README
explains how to install from the repository.

## Quick look

```python
import btoon

rows = [{"id": i, "name": f"user{i}", "active": i % 2 == 0} for i in range(1000)]
data = btoon.encode(rows)   # 11,561 bytes; MessagePack needs 27,509 and JSON 42,281
assert btoon.decode(data) == rows
```

The same bytes decode identically in C++, Node.js, the browser, Go and PHP.

## Contributing

Issues and pull requests are welcome in every repository. Format changes start in
btoon-core: first [the spec](https://github.com/BTOON-project/btoon-core/blob/main/docs/SPEC.md),
then the conformance vectors, then each implementation.
[IMPLEMENTATION-GUIDE.md](https://github.com/BTOON-project/btoon-core/blob/main/docs/IMPLEMENTATION-GUIDE.md)
covers writing a new library.

## License

MIT. See each repository's `LICENSE` file.
