# Sentinel-3 Extension Specification

- **Title:** Sentinel-3
- **Identifier:** <https://stac-extensions.github.io/sentinel-3/v0.2.0/schema.json>
- **Field Name Prefix:** s3
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Deprecated
- **Owner**: @m-mohr

This document explains the Sentinel-3 Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

> \[!CAUTION]
> This extension is deprecated!

- [Examples](examples/)
- [JSON Schema](json-schema/schema.json) (todo)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name               | Type            | Description                                                  |
| ------------------------ | --------------- | ------------------------------------------------------------ |
| s3:bright                | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:closed_sea            | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:coastal               | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:continental_ice       | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:cosmetic              | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:dubious_samples       | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:duplicated            | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:fresh_inland_water    | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:invalid               | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:land                  | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:open_ocean            | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:out_of_range          | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:saline_water          | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:saturated             | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:tidal_region          | number          | **DEPRECATED.** Use `statistics` instead                     |
| s3:product_type          | string          | **DEPRECATED.** Use `product:type` instead                   |
| s3:product_name          | string          | **DEPRECATED.** Use `product:type` instead                   |
| s3:processing_timeliness | string          | **DEPRECATED.** Use `product:timeliness` and `product:timeliness_category` instead |
| s3:lrm_mode              | number          | **DEPRECATED.** Use the [Altimetry extension](https://github.com/stac-extensions/altimetry) instead. |
| s3:sar_mode              | number          | **DEPRECATED.** Use the [Altimetry extension](https://github.com/stac-extensions/altimetry) instead. |
| s3:gsd                   | see description | **DEPRECATED.** Use `gsd` instead                            |
| s3:snow_or_ice           | number          | **DEPRECATED** Use `eo:snow_cover` instead                   |

The fields that are deprecated in favor of the `statistics` field as defined in
[common metadata](https://github.com/radiantearth/stac-spec/blob/dev/commons/common-metadata.md#statistics-object)
should remove the `s3:` prefix and use the remainders as the key name in the Statistics Object,
so for example `fresh_inland_water` instead of `s3:fresh_inland_water`.

**s3:gsd**: The data type differs between the products:

- *integer* used in olci-wfr and olci-lfr - **DEPRECATED** Use gsd instead.
- [SRAL GSD Object](#sral-gsd-object) used in sral-wat and sral-lan
- [Synergy GSD Object](#synergy-gsd-object) for synergy-v10, synergy-syn, synergy-aod, synergy-vg1 and synergy-vgp
- [SLSTR GSD Object](#slstr-gsd-object) for slstr-lst, slstr-frp and slstr-wst

### Altimetry Band Object

**DEPRECATED** Use eo:bands instead.

| Field Name       | Type   | Description            |
| ---------------- | ------ | ---------------------- |
| band_width       | number |                        |
| description      | string | Detailed multi-line description to explain the band. [CommonMark 0.29](http://commonmark.org/) syntax MAY be used for rich text representation. |
| frequency_band   | string | `Ku`, `C`, ...         |
| center_frequency | number | e.g. 5.41, 13.575, ... |

### SRAL GSD Object

**DEPRECATED.** Use `gsd` instead, usually defaulting to the value for along-track.

| Field Name   | Type    | Description   |
| ------------ | ------- | ------------- |
| along-track  | integer | **REQUIRED.** |
| across-track | integer | **REQUIRED.** |

### Synergy GSD Object

**DEPRECATED.** Use `gsd` instead, usually defaulting to the value for OLCI.

| Field Name | Type                                  | Description   |
| ---------- | ------------------------------------- | ------------- |
| OLCI       | integer                               | **REQUIRED.** |
| SLSTR      | [SLSTR GSD Object](#slstr-gsd-object) | **REQUIRED.** |

### SLSTR GSD Object

**DEPRECATED.** Use `gsd` instead.

| Field Name      | Type    | Description   |
| --------------- | ------- | ------------- |
| S1-S6           | integer | **REQUIRED.** |
| S7-S9 and F1-F2 | integer | **REQUIRED.** |


## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
