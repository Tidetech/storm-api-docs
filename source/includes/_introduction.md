# Introduction

**Version:** v1

The Tidetech Storm V1 API is a <a href='https://en.wikipedia.org/wiki/Representational_state_transfer'>RESTful web service</a> providing access to the latest data on tropical rotating storm activity for all ocean basins worldwide.

Forecasts are available out to 5 days/120 hours, or until the storm is expected to dissipate if less than 120 hours.

A list of currently active storms is provided via the <a href="#v1-active">`/v1/active`</a> endpoint.

Metadata for each active storm can be accessed from <a href="#v1-storm-id">`/v1/storm/{id}`</a> and is updated 4 times/day for the Northern hemisphere, and 2 times/day for the Southern hemisphere. See the <a href="#metadata">Metadata</a> section for more details.

The <a href="https://tools.ietf.org/html/rfc7946">GeoJSON</a> representation of each storm contains:
* Past storm tracks (lines)
* Forecast storm tracks (lines)
* Past storm positions and categories (points)
* Forecast storm positions including <a href="#categories">storm categories</a>, movement speed and direction at each forecast interval (0, 12, 24, 36, 48, 72, 96, 120 hours)
* Forecast Error Boundaries for each forecast interval (lines)
* Forecast Peak Gust Fields for the entire forecast (polygons)
