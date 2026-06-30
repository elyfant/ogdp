# OGDP

**Ocean Glider Data Pipeline**

OGDP is an open-source realtime processing pipeline for autonomous ocean gliders.

The project automates the journey from realtime telemetry to community-standard scientific data products. It is designed to be robust, reproducible, and extensible, building upon established community tools wherever possible instead of reimplementing existing solutions.

> **Project Status:** 🚧 Early development

---

## Vision

OGDP aims to provide a complete realtime processing pipeline for ocean gliders, including:

* Realtime data ingestion
* Automated processing
* Quality control
* Community-standard data products
* Database integration
* Mission analytics
* Open and reproducible workflows

The project is being developed with scientific transparency, operational robustness, and long-term maintainability as primary design goals.

---

## Design Principles

OGDP follows several core principles:

* **Raw data is immutable.**

  * The realtime raw archive is never modified.

* **Derived products are reproducible.**

  * All processing outputs can be regenerated from the raw archive.

* **Community standards first.**

  * Use established tools and standards wherever practical (e.g. PyGlider, OG1).

* **Small, composable components.**

  * Each module has a single responsibility.

* **Operational robustness over optimisation.**

  * Reliability and recoverability are prioritised over maximum performance.

* **Automation by default.**

  * Minimise manual intervention from data acquisition through to product generation.

---

## High-Level Architecture

```text
                 SFMC
                   │
                   ▼
        Realtime Event Listener
                   │
                   ▼
                 rsync
                   │
                   ▼
          Realtime Raw Archive
                   │
                   ▼
           Mission Resolution
                   │
                   ▼
             Processing Pipeline
                   │
      ┌────────────┼────────────┐
      ▼            ▼            ▼
   QC & Corrections OG1 Export Database
                   │
                   ▼
          Mission Products
```

The ingestion layer is intentionally lightweight. Its responsibility is to safely mirror realtime data from the glider communication server into the local raw archive.

Scientific processing is performed as an independent stage.

---

## Current Scope

The current focus of OGDP is **realtime processing**.

This includes:

* SFMC event monitoring
* Automated rsync synchronisation
* Realtime processing
* Mission management
* OG1 product generation
* Operational analytics

Delayed-mode processing following vehicle recovery is considered a separate workflow and is currently outside the scope of this repository.

---

## Planned Features

* Realtime ingestion service
* Mission processing pipeline
* PyGlider integration
* Automated QC framework
* Thermal lag correction
* OG1 NetCDF generation
* Database integration (OGDB)
* Parquet mission products
* Battery endurance analysis
* Mission reporting
* NMDC integration

---

## Repository Structure

```text
ogdp/

├── config/
├── docs/
├── examples/
├── js/
├── python/
├── scripts/
├── tests/
└── docker/
```

The repository contains source code, documentation, configuration templates, and tests only.

Mission data, raw archives, and generated products are intentionally stored outside the repository.

---

## Technology Stack

### JavaScript / Node.js

* SFMC event listener
* Realtime ingestion
* rsync orchestration

#### Prerequisites

The OGDP ingestion service depends on the Teledyne SFMC Node.js SDK.

This SDK is **not distributed with OGDP** and must be obtained separately as part of the Teledyne SFMC installation.

Once installed, update `js/package.json` (or your local configuration) to point to the location of `sfmc.tgz`.

See `docs/user-guide/sfmc-installation.md` for details.


### Python

* Processing pipeline
* PyGlider integration
* Quality control
* OG1 export
* Database integration
* Analytics

---

## Documentation

Project documentation is located in the `docs/` directory.

Architecture decisions are recorded as Architecture Decision Records (ADRs), allowing the reasoning behind major design choices to be preserved alongside the code.

---

## Contributing

OGDP is being developed as an open-source project.

Contributions, suggestions, bug reports, and discussions are welcome as the project matures.

---

## License

License to be determined.
