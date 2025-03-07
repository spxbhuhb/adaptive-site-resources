# Changelog

## General

Changelog is now a document resource for site. I'll keep it this way until I move it into
a database.

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
