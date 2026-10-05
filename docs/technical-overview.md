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

## Disclosure and enforcement boundaries

Operation-specific authority checks govern actions taken through the participating runtime. Provenance and restriction records make the basis of a permitted operation inspectable; they do not make a restriction self-enforcing after information is copied into a system outside that boundary. Deployment assurance therefore depends on the integrity of the enforcing runtime, its policy inputs and the receiving environment. Authentication and integrity checks establish properties of an exchange, not the truth of a contribution or the future conduct of its recipient.

Local source retention also does not establish cumulative privacy. Several individually permitted releases can jointly reveal protected information, including when combined with outside knowledge or information shared among recipients. The design requires disclosure to be considered across related releases and available recipient and purpose context, rather than treating each operation as an isolated decision. This does not imply complete visibility into a recipient’s outside knowledge. The public evidence does not establish a quantitative leakage bound, a differential-privacy guarantee or a validated defence against arbitrary reconstruction from accumulated outputs.

Queries are themselves disclosures: their content, destination or pattern may reveal what a participant knows, suspects or intends to investigate. Query confidentiality is a design requirement alongside response confidentiality. The published localhost transport and lifecycle tests do not establish protection against traffic analysis, recipient inference or disclosure through Query metadata. No claim of anonymous or cryptographically private querying is made here.

## Adversarial scope

The relevant risks extend beyond accidental errors to participants that submit false or misleading evidence, conceal dependence, collude, probe disclosure limits or attempt to poison shared reasoning. A well-formed, attributable contribution can still be false. The design requires suspected manipulation or poisoned evidence to be quarantined, contested or represented as uncertain, according to the applicable rules. Suspicion does not itself establish falsity.

These requirements should not be read as demonstrated resistance to malicious participants. The public evidence does not establish a complete adversary model with corruption thresholds, collusion bounds or security proofs. It also does not demonstrate robust inference under coordinated deception or compromised runtimes. Those claims require explicit assumptions and adversarial evaluation before deployment assurance can be made.

## Relationship to established work

The constituent problems have substantial prior art. [Dong, Berti-Equille and Srivastava’s work on source dependence](https://www.vldb.org/pvldb/vol2/vldb09-pvldb47.pdf) studies truth discovery when sources may copy one another. [Federated analytics](https://research.google/blog/federated-analytics-collaborative-data-science-without-data-collection/) computes across locally held data without collecting the underlying records centrally. [Secure multiparty computation](https://csrc.nist.gov/Projects/pec) addresses joint computation over parties’ inputs under cryptographic security assumptions. [International Data Spaces](https://internationaldataspaces.org/wp-content/uploads/IDS-Reference-Architecture-Model-3.0-2019.pdf) addresses data sovereignty, controlled exchange and trust among participants.

StrataDOME’s stated focus is the combination of attributable inference, persistent uncertainty, directed inquiry and distinct disclosure and action authority across institutional domains. This is an architectural emphasis rather than a claim that dependency-aware reasoning or data sovereignty is new. No comparative benchmark or equivalence to MPC security guarantees is claimed; those comparisons require defined workloads, common assumptions and measured results.

## Public specification boundary

The descriptions here explain roles, relationships and selected implementation behavior. Normative record schemas, complete state-transition rules and a reproducible definition of the inference procedure are not published in this repository. It is therefore not currently sufficient to build an  
interoperable implementation or verify full conformance from public materials alone. Published test summaries provide bounded evidence, not a substitute for those artifacts.
