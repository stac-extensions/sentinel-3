# Sentinel-3 Extension Specification

- **Title:** Sentinel-3
- **Identifier:** <https://stac-extensions.github.io/sentinel-3/v1.0.0/schema.json>
- **Field Name Prefix:** s3
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr

This document explains the Sentinel-3 Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

The intention of the first version of the specification is to define the existing behavior of
the properties prefixed with `s3` as created by the [stactools-sentinel3](https://github.com/stactools-packages/sentinel3) package and used by
[Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/api/stac/v1). Future versions
will aspire to standardize fields such as the numerous coverage calculations into separate extensions that are not specific to Sentinel-3.

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

| Field Name               | Type            | Description                                                  | Applies to                                                   |
| ------------------------ | --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| s3:product_type          | string          | One of: `OL_2_WFR___`, `SR_2_WAT___`, `SR_2_LAN___`, `SL_2_FRP___`, `SY_2_V10___`, `OL_2_LFR___`, `SL_2_LST___`, `SY_2_VGP___`, `SL_2_WST___`, `SY_2_SYN___`, `SY_2_AOD___`, `SY_2_VG1___` | all                                                          |
| s3:product_name          | string          | One of: `olci-wfr`, `sral-wat`, `sral-lan`, `slstr-frp`, `synergy-v10`, `olci-lfr`, `slstr-lst`, `synergy-vgp`, `slstr-wst`, `synergy-syn`, `synergy-aod`, `synergy-vg1` | all                                                          |
| s3:processing_timeliness | string          | One of: `NT`, ...                                            | all                                                          |
| s3:gsd                   | see description |                                                              | all                                                          |
| s3:lrm_mode              | number          |                                                              | sral-wat, sral-lan                                           |
| s3:sar_mode              | number          |                                                              | sral-wat, sral-lan                                           |
| s3:bright                | number          |                                                              | olci-wfr                                                     |
| s3:closed_sea            | number          |                                                              | sral-wat, sral-lan                                           |
| s3:coastal               | number          |                                                              | olci-lfr, olci-wfr, slstr-frp, slstr-lst, synergy-vgp, slstr-wst, synergy-syn |
| s3:continental_ice       | number          |                                                              | sral-wat, sral-lan                                           |
| s3:cosmetic              | number          |                                                              | olci-lfr, olci-wfr, slstr-frp, slstr-lst, slstr-wst          |
| s3:dubious_samples       | number          |                                                              | olci-lfr, olci-wfr                                           |
| s3:duplicated            | number          |                                                              | olci-lfr, olci-wfr, slstr-frp, slstr-lst, slstr-wst          |
| s3:fresh_inland_water    | number          |                                                              | olci-lfr, olci-wfr, slstr-frp, slstr-lst, synergy-vgp, slstr-wst, synergy-syn |
| s3:invalid               | number          |                                                              | olci-lfr, olci-wfr                                           |
| s3:land                  | number          |                                                              | olci-lfr, olci-wfr, sral-wat, sral-lan, slstr-frp, synergy-v10, slstr-lst, synergy-vgp, slstr-wst, synergy-syn, synergy-aod, synergy-vg1 |
| s3:open_ocean            | number          |                                                              | sral-wat, sral-lan                                           |
| s3:out_of_range          | number          |                                                              | slstr-lst, slstr-wst                                         |
| s3:saline_water          | number          |                                                              | olci-lfr, olci-wfr, slstr-frp, slstr-lst, synergy-vgp, slstr-wst, synergy-syn, synergy-aod |
| s3:saturated             | number          |                                                              | olci-lfr, olci-wfr, slstr-frp, slstr-lst, slstr-wst          |
| s3:tidal_region          | number          |                                                              | olci-lfr, olci-wfr, slstr-frp, slstr-lst, synergy-vgp, slstr-wst, synergy-syn |
| s3:snow_or_ice           | number          | **DEPRECATED** Use eo:snow_cover instead                     | synergy-v10, synergy-vgp, synergy-vg1                        |

**s3:gsd**: The data type differs between the products:
- *integer* used in olci-wfr and olci-lfr - **DEPRECATED** Use gsd instead.
- [SRAL GSD Object](#sral-gsd-object) used in sral-wat and sral-lan
- [Synergy GSD Object](#synergy-gsd-object) for synergy-v10, synergy-syn, synergy-aod, synergy-vg1 and synergy-vgp
- [SLSTR GSD Object](#slstr-gsd-object) for slstr-lst, slstr-frp and slstr-wst

---

- [ ] Catalogs
- [ ] Collections
- [ ] Item Properties (incl. Summaries in Collections)
- [x] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name            | Type                                              | Description                           |
| --------------------- | ------------------------------------------------- | ------------------------------------- |
| s3:shape              | [integer]                                         | **DEPRECATED** Use proj:shape instead |
| s3:spatial_resolution | [number]                                          | **DEPRECATED**                        |
| s3:altimetry_bands    | [[Altimetry Band Object](#altimetry-band-object)] | **DEPRECATED** Use eo:bands instead   |

### Altimetry Band Object

| Field Name       | Type   | Description            |
| ---------------- | ------ | ---------------------- |
| band_width       | number |                        |
| description      | string |                        |
| frequency_band   | string | `Ku`, `C`, ...         |
| center_frequency | number | e.g. 5.41, 13.575, ... |

### SRAL GSD Object

| Field Name   | Type    | Description |
| ------------ | ------- | ----------- |
| along-track  | integer |             |
| across-track | integer |             |

### Synergy GSD Object

| Field Name | Type                                  | Description |
| ---------- | ------------------------------------- | ----------- |
| OLCI       | integer                               |             |
| SLSTR      | [SLSTR GSD Object](#slstr-gsd-object) |             |

### SLSTR GSD Object

| Field Name      | Type    | Description |
| --------------- | ------- | ----------- |
| S1-S6           | integer |             |
| S7-S9 and F1-F2 | integer |             |

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
