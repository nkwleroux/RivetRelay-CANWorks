# CANWorks

A reusable embedded CAN subsystem rather than an isolated demonstration. It owns protocol definitions, MCU encoding/decoding, Linux SocketCAN support, diagnostics, simulation, and fault fixtures.

## Languages

- C for portable MCU codecs.
- C++20 for Linux gateway components and tools.
- Python for code generation, test traffic, and analysis.
- DBC for human- and tool-readable CAN message definitions.

## Suggested structure

```text
canworks/
├── dbc/                  # Versioned CAN database
├── embedded/             # Allocation-free C/C++ codecs
├── gateway/              # SocketCAN C++ library/service
├── generators/           # DBC-to-code tooling
├── tools/                # Record, replay, inspect, fault inject
├── tests/
│   ├── unit/
│   └── vcan/
├── .gitignore
├── ARCHITECTURE.md
├── CMakeLists.txt
└── README.md
```

## Potential libraries and packages

- Linux SocketCAN headers and `can-utils`
- cantools and python-can
- fmt and spdlog
- Boost.Asio or standalone Asio when asynchronous integration is needed
- CLI11 for command-line tools
- Catch2 or GoogleTest
- DBC code generator such as cantools-generated C sources, after validating its output constraints

The embedded codec should avoid heap allocation and remain usable without Linux libraries.

## Independent demonstration

Create several nodes on Linux `vcan`, replay captures, decode a DBC, detect missing heartbeats, and demonstrate malformed/late/duplicate traffic handling.

## Integration

- ControlBench links only the embedded codec.
- HILForge uses Python CAN tooling and shared fault fixtures.
- LinuxEdge links the SocketCAN gateway library.

