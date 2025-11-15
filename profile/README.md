<div align="center">

# BTOON Project

**Binary Transport for TOON** — A high-performance binary serialization format

[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![C++ Standard](https://img.shields.io/badge/C++-20-blue.svg)](https://en.cppreference.com/w/cpp/20)
[![Status](https://img.shields.io/badge/status-active-brightgreen.svg)](https://github.com/BTOON-project)

</div>

---

## 🌟 What is BTOON?

**BTOON** (Binary TOON) is a high-performance binary serialization format that extends [MessagePack](https://msgpack.org/) with custom tabular data optimization. Built for the [TOON format](https://github.com/toon-format/toon), BTOON provides **20-40% size reduction** for uniform tabular datasets while maintaining full MessagePack compatibility.

### Key Features

- 🚀 **High Performance** — 4-7x faster than JSON, comparable to MessagePack
- 📦 **MessagePack Compatible** — Fully compliant with the MessagePack specification
- 📊 **Tabular Optimization** — Custom extension for compact tabular data encoding
- 🔒 **Type Safe** — Comprehensive, modern C++20 type system
- 🌐 **Multi-Language** — Language bindings for Python, Node.js, JavaScript, Go, and PHP
- 🎯 **Zero-Copy Decoding** — Efficient `std::span` API for minimal allocations
- 📝 **Schema Validation** — Validate data against user-defined schemas
- 🌊 **Streaming API** — Efficiently encode and decode sequences of objects

---

## 📚 Repositories

### Core Library
- **[btoon-core](https://github.com/BTOON-project/btoon-core)** — C++20 core library with C-API for language bindings

### Language Bindings
- **[btoon-python](https://github.com/BTOON-project/btoon-python)** — Python bindings (pybind11)
- **[btoon-nodejs](https://github.com/BTOON-project/btoon-nodejs)** — Node.js bindings (N-API)
- **[btoon-javascript](https://github.com/BTOON-project/btoon-javascript)** — JavaScript/WASM bindings
- **[btoon-go](https://github.com/BTOON-project/btoon-go)** — Go bindings (cgo)
- **[btoon-php](https://github.com/BTOON-project/btoon-php)** — PHP bindings

### Web & Tools
- **[btoon-web](https://github.com/BTOON-project/btoon-web)** — Modern web interface built with React + Vite

---

## 🚀 Quick Start

```cpp
#include "btoon/btoon.h"

using namespace btoon;

// Create a value
Value data = Map{
    {"name", String("Alice")},
    {"age", Int(30)},
    {"active", Bool(true)}
};

// Encode
auto encoded = encode(data);

// Decode
auto decoded = decode(encoded);
```

---

## 🤝 Contributing

BTOON is in early stages, so every bug report, idea, or pull request has outsized impact! We welcome contributions of all kinds:

- 🐛 **Bug Reports** — Help us improve stability
- 💡 **Feature Ideas** — Share your use cases and needs
- 📖 **Documentation** — Improve docs and examples
- 🔧 **Code Contributions** — Submit PRs for features or fixes
- 🎨 **Design & UX** — Enhance the web interface

### How to Contribute

1. Fork the repository you want to contribute to
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes with clear commit messages
4. Open a pull request with context and details
5. Be kind and transparent — we ship in public to learn together

**No contribution is too small.** Docs improvements, design tweaks, and roadmap suggestions are all valuable when building something new.

---

## 📖 Resources

- 📘 [Technical Specification](https://github.com/BTOON-project/btoon-core/blob/main/docs/btoon-spec.md)
- 🗺️ [Roadmap](https://github.com/BTOON-project/btoon-core/blob/main/docs/roadmap.md)
- 🌐 [Web Interface](https://btoon.dev) *(coming soon)*
- 📝 [API Documentation](https://github.com/BTOON-project/btoon-core#api-reference)

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built with ❤️ by the BTOON community**

[Website](https://btoon.dev) • [Documentation](https://github.com/BTOON-project/btoon-core) • [Issues](https://github.com/BTOON-project/btoon-core/issues)

</div>

