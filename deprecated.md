# Deprecated fields in the Sentinel-3 Extension Specification

The following document describes all deprecated fields and objects that had been defined before.
For the sake of simplicity the deprecated content has been moved to this separate document.

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name               | Type            | Description                                                  |
| ------------------------ | --------------- | ------------------------------------------------------------ |
| s3:product_type          | string          | **DEPRECATED.** Use `product:type` instead                   |
| s3:product_name          | string          | **DEPRECATED.** Use `product:type` instead                   |
| s3:processing_timeliness | string          | **DEPRECATED.** Use `product:timeliness` and `product:timeliness_category` instead |
| s3:lrm_mode              | number          | **DEPRECATED.** Use the [Altimetry extension](https://github.com/stac-extensions/altimetry) instead. |
| s3:sar_mode              | number          | **DEPRECATED.** Use the [Altimetry extension](https://github.com/stac-extensions/altimetry) instead. |
| s3:gsd                   | see description | **DEPRECATED.** Use `gsd` instead                            |
| s3:snow_or_ice           | number          | **DEPRECATED** Use `eo:snow_cover` instead                   |

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
