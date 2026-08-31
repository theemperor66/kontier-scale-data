# kontier-scale-data

Synthetic `billing_events` dataset for the [kontier-ri](https://github.com/theemperor66/kontier-ri)
100M-row scale proof. **100,000,000 rows**, 8 hive partitions (`quarter=2024-Q1` … `quarter=2025-Q4`),
Parquet + ZSTD, row groups of 4,000,000 rows.

Columns: `event_ts TIMESTAMP` (minute precision), `customer_id BIGINT`, `country VARCHAR(10 values)`,
`plan VARCHAR(4)`, `gateway VARCHAR(4)`, `status VARCHAR(succeeded|failed|refunded)`, `amount_cents BIGINT`,
plus the `quarter` hive partition column.

Served via GitHub Pages (CORS `*`, HTTP Range supported), so DuckDB-WASM in the browser
range-reads only the parquet footers and row groups a query needs.

Fully synthetic data, generated deterministically by
[`scripts/generate-scale-data.sh`](https://github.com/theemperor66/kontier-ri/blob/main/scripts/generate-scale-data.sh). No license restrictions (CC0).
