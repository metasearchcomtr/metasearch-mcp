# Tools and targets

## Feed preparation

### `detect_feed_format`
Detect JSON, NDJSON, XML, CSV, or TSV.

### `normalize_hotel_feed`
Parse a supplier/platform feed and map common field aliases into the canonical hotel record surface without rewriting the source payload.

## Validation

### `validate_feed`
Validate against a selected target.

Target-specific aliases:

- `validate_google_hotel_center_list`
- `validate_wego_hotel_feed`
- `validate_trivago_hotel_data`
- `validate_meta_catalog`
- `validate_criteo_catalog`
- `validate_hotel_master_data`

## Comparison and remediation

### `compare_feed_readiness`
Run one payload through several rule packs and compare scores/issues.

### `compare_platform_requirements`
Compare known published/readiness requirements before designing a mapping.

### `suggest_feed_fixes`
Return deterministic remediation steps derived from validation issue codes.

## Evidence levels

Google Hotel Center, Wego and trivago rule packs use published platform documentation where documented. Meta and Criteo are readiness/mapping pre-checks and are not represented as official certification.
