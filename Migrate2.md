# Migrating v1 Plugins to v2

The API of VCV Rack v2 has been designed to be nearly backward-compatible with v1 plugins, so updating your plugin to v2 likely only involves the following step and a recompile.

## Update plugin version to v2

The major version number (`vMAJOR.MINOR.REVISION`) of your plugin must match the major version of Rack, so change the version number in your plugin's `plugin.json` manifest to `2`.
For example, change
```json
{
  "slug": "Fundamental",
  "version": "1.2.3",
  ...
```
to
```json
{
  "slug": "Fundamental",
  "version": "2.0.0",
  ...
```
If you wish, you may keep the minor and revision numbers unchanged, e.g. `2.2.3`.

Download the latest [Rack v2 SDK](https://vcvrack.com/downloads/).
Clean and compile the plugin.
```bash
export RACK_SDK=/path/to/Rack-SDK
make clean
make dist
```
If your plugin compiles successfully, you are ready to test and release.
Or, you may take advantage of new v2 features below.


## Optional v2 API features

### Port labels

TOOD

### Light labels

TODO

### TODO

```bash
perl -i -pe 's/(\w+)_PARAM\b/PARAM_$1/g' src/*
perl -i -pe 's/(\w+)_BUTTON\b/BUTTON_$1/g' src/*
perl -i -pe 's/(\w+)_SWITCH\b/SWITCH_$1/g' src/*
perl -i -pe 's/(\w+)_INPUT\b/INPUT_$1/g' src/*
perl -i -pe 's/(\w+)_OUTPUT\b/OUTPUT_$1/g' src/*
perl -i -pe 's/(\w+)_LIGHT\b/LIGHT_$1/g' src/*
```
