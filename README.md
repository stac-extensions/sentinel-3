# Sentinel-3 Extension Specification

- **Title:** Sentinel-3
- **Identifier:** <https://stac-extensions.github.io/sentinel-3/v0.2.0/schema.json>
- **Field Name Prefix:** s3
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr

This document explains the Sentinel-3 Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

> \[!CAUTION]
> The intention of the first version of the specification was to reflect the existing behavior of the properties
> prefixed with `s3` as implemented by the [stactools-sentinel3](https://github.com/stactools-packages/sentinel3) package.
> The following version deprecated most of the fields in favor of other extensions that are not specific to Sentinel-3.
> The remaining fields are for statistical purposes.
> If you want to expose the statistal fields, this extension is currently the best approach until a
> generic approach for STAC has been defined.
> For all other fields the recommended alternatives should be preferred.

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

| Field Name            | Type   | Description                                                  |
| --------------------- | ------ | ------------------------------------------------------------ |
| s3:bright             | number | Percentage of bright pixels (0-100)                          |
| s3:closed_sea         | number | Percentage of pixels classified as closed sea (0-100)        |
| s3:coastal            | number | Percentage of pixels classified as coastal (0-100)           |
| s3:continental_ice    | number | Percentage of pixels classified as continental ice (0-100)   |
| s3:cosmetic           | number | Percentage of cosmetic pixels (0-100)                        |
| s3:dubious_samples    | number | Percentage of dubious pixels (0-100)                         |
| s3:duplicated         | number | Percentage of duplicated pixels (0-100)                      |
| s3:fresh_inland_water | number | Percentage of pixels classified as fresh inland water (0-100) |
| s3:invalid            | number | Percentage of invalid pixels (0-100)                         |
| s3:land               | number | Percentage of pixels classified as land (0-100)              |
| s3:open_ocean         | number | Percentage of pixels classified as open ocean (0-100)        |
| s3:out_of_range       | number | Percentage of out-of-range pixels (0-100)                    |
| s3:saline_water       | number | Percentage of pixels classified as saline water (0-100)      |
| s3:saturated          | number | Percentage of saturated pixels (0-100)                       |
| s3:tidal_region       | number | Percentage of pixels classified as tidal regions (0-100)     |

> \[!NOTE]
> Various fields and objects in this extensions have been deprecated.
> Please see the [document about deprecated fields](deprecated.md) for more information.

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
