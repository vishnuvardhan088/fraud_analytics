# Medallion Lakehouse Framework – Microsoft Fabric

This repository implements a **production-grade Medallion Architecture**
(Bronze → Silver → Gold) using **Microsoft Fabric Lakehouse**.

## Key Features
- Separate Lakehouses for governance (LH_BRONZE, LH_SILVER, LH_GOLD)
- Metadata-driven ingestion
- Schema contract enforcement
- Quarantine for bad data
- Type-1 current tables
- Type-2 history (SCD) tables
- Centralized audit logging
- BI-ready Gold layer

## Architecture
See `diagrams/architecture.md`

## Lakehouses
| Layer | Purpose |
|-----|--------|
| LH_BRONZE | Raw, immutable ingestion |
| LH_SILVER | Validated, standardized, historical |
| LH_GOLD | Curated analytics + control plane |

## Execution Order
1. `00_control_setup_gold`
2. `01_register_entities_gold`
3. `02_schema_contract_setup`
4. `03_schema_contract_seed`
5. `10_ingest_to_bronze`
6. `20_bronze_to_silver_contract_scd`
7. `30_silver_to_gold_framework`

## Pipeline
Use Fabric Data Pipeline to orchestrate:
Bronze → Silver → Gold

## Author
Built as a real-world Microsoft Fabric data engineering framework.
