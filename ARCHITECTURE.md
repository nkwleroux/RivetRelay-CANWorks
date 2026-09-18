# CANWorks Architecture

## Layers

1. **Contract:** DBC, node IDs, timing, scaling, and compatibility policy.
2. **Embedded codec:** deterministic encoding/decoding with no dynamic allocation.
3. **Transport adapters:** MCU controller driver boundary and Linux SocketCAN.
4. **Supervision:** heartbeat, timeout, restart, and health state machines.
5. **Tooling:** simulation, capture, replay, diagnostics, and fault injection.

## Ownership rule

CANWorks owns CAN semantics but not ControlBench control logic, HILForge orchestration, LinuxEdge cloud translation, or SecureFleet device management.

