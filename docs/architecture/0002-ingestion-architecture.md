0002-ingestion-architecture.md

# Ingestion Architecture

Status
Accepted

Context

The SFMC API supports file transfer, but maintaining file state,
timestamps and partial downloads increases complexity.

Decision

Use the SFMC API only for connection events.

Use rsync as the authoritative synchronization mechanism.

Consequences

+ Simpler implementation
+ Easy recovery after failures
+ Local filesystem mirrors SFMC

Disadvantages

- Slightly slower than API transfer
