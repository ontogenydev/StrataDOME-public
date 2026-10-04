# Technical overview

## Runtime

The reference implementation is a Python system with explicit package boundaries. Protocol and provenance sit inside the semantic core; infrastructure adapters point inward toward those contracts; runtime composition remains separate from both. This keeps implementation technology from becoming semantic authority.

## Persistence

Local persistence uses bounded SQLite adapters. Sender-side state is kept separate from the receiver's durable record, and delivery attempts are tracked independently of both. Persistence adapters do not own semantic authority.

## Transport

Current integration work uses authenticated IPv4 loopback HTTP as a deliberately narrow reference transport. Transport success alone is not treated as evidence of semantic acceptance or durable receipt.

## Authority checks

Before a protected operation proceeds, the runtime rechecks that the exact use being attempted is still permitted in its current context. A prior permission does not become a standing entitlement. Transforming the material does not automatically broaden what may be done with it.

## Query lifecycle

A Query begins as an unresolved gap in shared understanding. It is registered before delivery and must be durably acknowledged by the receiving side before it can contribute to later shared state. Each stage can be verified and resumed independently rather than disappearing inside one opaque transaction.

## Evidence discipline

Runtime evidence is kept at the level it actually proves. Successful transport proves only transport. A persisted receipt proves receipt, not acceptance or completion. Partial integration results stay partial.