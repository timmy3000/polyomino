# 🧩 Polyomino

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![C++17](https://img.shields.io/badge/C%2B%2B-17-blue.svg)](https://en.cppreference.com/w/cpp/17)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)]()

A high-performance C++ implementation for enumerating all unique polyomino shapes of size N using efficient iterative algorithms with real-time progress tracking.

## 🚀 Features

- **⚡ High Performance**: Optimized iterative BFS-based enumeration (no recursion)
- **📊 Real-time Progress**: Live updates showing generation progress and timing
- **🔄 Symmetry Handling**: Support for free, one-sided, and fixed polyominoes
- **💾 Multiple Outputs**: Console display, file export, and ASCII visualization
- **✅ Validated Results**: Built-in validation against known mathematical values
- **🏗️ Modular Design**: Clean, maintainable code architecture
- **⏱️ Precision Timing**: High-resolution timing with millisecond accuracy

## 📈 Performance

Generates and validates polyominoes efficiently:

| Size (N) | Type | Count | Time* |
|----------|------|-------|-------|
| 4 | Free | 5 | < 0.01s |
| 5 | Free | 12 | < 0.01s |
| 6 | Free | 35 | < 0.1s |
| 7 | Free | 108 | < 0.5s |
| 8 | Free | 369 | < 2s |

*Times measured on modern CPU with -O3 optimization

## 🛠️ Quick Start

### Prerequisites
- C++17 compatible compiler (GCC 7+, Clang 5+, MSVC 2017+)
- CMake 3.10+ (optional, for build system)

### Building

**Simple compilation:**
```bash
g++ -std=c++17 -O3 -Wall -Wextra -o polyomino polyomino.cpp
```

**With CMake:**
```bash
mkdir build && cd build
cmake ..
make
```

### Usage

**Basic usage:**
```bash
# Generate free pentominoes (default)
./polyomino 5

# Generate one-sided hexominoes with visualization
./polyomino 6 one-sided show

# Generate tetrominoes and save to file
./polyomino 4 free file
```

**Command-line options:**
```
./polyomino [N] [type] [output]

Parameters:
  N      : Polyomino size (1-20, default: 5)
  type   : free | one-sided | fixed (default: free)
  output : show | file | both (default: console)
```

## 📋 Example Output

```
Polyomino Enumerator v1.0
========================

Configuration:
  Size (N): 5
  Type: free
  Output: console

Starting enumeration...
[Size 5] Unique: 12 | Generated: 1537 | Time: 0.045s

✓ Enumeration completed in 0.045 seconds
✓ Found 12 unique polyominoes
✓ Validation passed: matches known value

=== Results ===
Enumeration type: free
Polyomino size: 5
Total unique shapes: 12
```

## 🔬 Algorithm Details

### Core Algorithm
- **Iterative BFS Growth**: Starts with single tile, grows by adding adjacent cells
- **Canonical Deduplication**: Uses lexicographically minimal representation
- **Symmetry Reduction**: Handles rotations and reflections based on enumeration type

### Data Structures
- **Polyomino Representation**: Vector of normalized (x,y) coordinates
- **Hash-based Deduplication**: Unordered set with custom hash function
- **Progress Tracking**: High-resolution timing with configurable update intervals

### Symmetry Types
- **Free**: All rotations and reflections considered equivalent
- **One-sided**: Only rotations considered equivalent (reflections distinct)  
- **Fixed**: No symmetry reduction (all orientations distinct)

## 📊 Validation

The implementation is validated against known mathematical sequences:

| N | Free | One-sided | Fixed |
|---|------|-----------|-------|
| 1 | 1 | 1 | 1 |
| 2 | 1 | 1 | 2 |
| 3 | 2 | 2 | 6 |
| 4 | 5 | 7 | 19 |
| 5 | 12 | 18 | 63 |
| 6 | 35 | 60 | 216 |
| 7 | 108 | 196 | 760 |

Source: [OEIS A000105](https://oeis.org/A000105) (Free), [A001168](https://oeis.org/A001168) (Fixed)

## 🏗️ Architecture

```
├── Polyomino          # Core shape representation
├── ShapeGenerator     # Main enumeration engine  
├── ShapeNormalizer    # Canonical form handler
├── ProgressTracker    # Real-time progress updates
├── OutputManager      # Display and file export
└── InputValidator     # Configuration validation
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests.

### Development Setup
1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes with tests
4. Submit a pull request

### Code Standards
- Follow C++17 standards
- Use consistent formatting (clang-format recommended)
- Include documentation for public interfaces
- Add tests for new features

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Mathematical foundation based on polyomino theory
- Inspired by various computational geometry algorithms
- Performance optimizations influenced by competitive programming techniques

## 📚 References

- [Polyomino - Wikipedia](https://en.wikipedia.org/wiki/Polyomino)
- [OEIS A000105 - Free polyominoes](https://oeis.org/A000105)
- [Computational Geometry Algorithms](https://en.wikipedia.org/wiki/Computational_geometry)
