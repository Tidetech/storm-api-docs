# Metadata

| key | value |
|-----|-------|
| **`id`** | The storm ID. This ID is unique across the API. |
| **`advisory`** | The UTC datetime of the most recent advisory for this storm. |
| **`is_active`** | Whether or not the storm is currently active. |
| **`name`** | The storm name. |
| **`basin`** | The ocean basin in which the storm is currently active. |
| **`category`** | The tropical cyclone classification of the storm as at the time of advisory. |
| **`forecast_hours`** | The number of hours in the forecast, based on the estimated duration of the storm, up to 120 hours. |
| **`geojson`** | Link to the GeoJSON representation of the storm forecast. |
| **`event_number`** | The seasonal event number of the storm within a basin. |
| **`position`** | The coordinates of the storm at the time of advisory. |
| **`movement`** | The movement speed and bearing at the time of advisory. |
| **`max_observed_category`** | The maximum tropical storm classification reached by the storm. |
| **`max_forecast_category`** | The maximum tropical storm classification forecasted for the storm. |
| **`name_list`** | All names assigned to a storm. Eg. `["TWENTYTHREE", "WALLACE"]`. |
| **`advisory_list`** | Record of advisory dates. |
