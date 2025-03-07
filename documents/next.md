# Changelog

## General

Changelog is now a document resource for site. I'll keep it this way until I move it into
a database.

## UI

- density dependent pixel operations moved from `AbstractAuiAdapter` to `DensityIndependentAdapter`
- `AuiRenderData` now uses `DensityIndependentAdapter` instead of `AbstractAuiAdapter`

## Graphics

### Canvas

#### New fragments

- `path`
- `transform`

#### New instructions

- `translate`
- `rotate`
- `scale`
- `matrix`
- `skewX`
- `skewY`

### SVG

#### Changes

- remove `svgFill`, use `fill` instead
- transforms and path commands moved to canvas

## Util

- various bugfixes and improvements for ByteArrayQueue and temporal
