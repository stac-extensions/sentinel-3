# Sentinel-3 Extension Specification

- **Title:** Sentinel-3
- **Identifier:** <https://stac-extensions.github.io/sentinel-3/v0.1.0/schema.json>
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

| Field Name            | Type   | Description |
| --------------------- | ------ | ----------- |
| s3:bright             | number |             |
| s3:closed_sea         | number |             |
| s3:coastal            | number |             |
| s3:continental_ice    | number |             |
| s3:cosmetic           | number |             |
| s3:dubious_samples    | number |             |
| s3:duplicated         | number |             |
| s3:fresh_inland_water | number |             |
| s3:invalid            | number |             |
| s3:land               | number |             |
| s3:open_ocean         | number |             |
| s3:out_of_range       | number |             |
| s3:saline_water       | number |             |
| s3:saturated          | number |             |
| s3:tidal_region       | number |             |

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
