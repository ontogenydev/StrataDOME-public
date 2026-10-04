# Technical overview

## Runtime

The reference implementation is a Python system divided into explicit implementation units for protocol, provenance, semantic ports, domain semantics, sovereignty, constitution, epistemics, Fields, Queries, effects, adapters, runtime composition, and conformance evidence.

## Persistence

Local persistence uses bounded SQLite adapters with separate responsibilities for sender state, receiver state, delivery attempts, and durable receipts. Persistence adapters do not own semantic authority.

## Transport

Current integration work uses authenticated IPv4 loopback HTTP as a deliberately narrow reference transport. Transport success alone is not treated as evidence of semantic acceptance or durable receipt.

## Authority checks

Protected operations are checked against the exact object, recipient, context, purpose, scope, currentness, onward-use conditions, derivation limits, and source-local constraints applicable to that operation.

## Query lifecycle

A Query is formed from a qualified epistemic gap, persistently registered, delivered under current authority, durably acknowledged by the receiving side, and later confirmed into shared epistemic state. These phases remain independently verifiable and resumable rather than being treated as one opaque transaction.

## Evidence discipline

Runtime evidence is retained as evidence of exactly what occurred. A transport event is not promoted into a durable receipt; a durable receipt is not promoted into operational acceptance; and partial integration results are not represented as completed end-to-end behavior.