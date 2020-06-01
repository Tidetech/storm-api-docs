# Accessing the API

The API can be accessed at <a href='https://api.tidetech.org/v2/'>https://api.tidetech.org/v2/</a>


## Accessing via browser

Explore the API by accessing the URLs provided in the response data. This is useful to get an understanding of the API structure, view metadata and even download forecasts, but you will need to access it programmatically to extract point and area data.

You can view dataset metadata and download forecast files in your browser by navigating to the index at https://api.tidetech.org/v2/ and following the links provided.

<aside class="notice">
You must authenticate in order to access non-public metadata, datasets and forecasts. See the <a href='#browser-authentication'>Browser authentication</a> section for more details.
</aside>


## Accessing via curl

`curl` is a popular lightweight command line tool used to transfer data to or from servers. It is available for all major operating systems and can be used to test the `shell` API request examples.

<aside class="notice">
As the files served from our `forecast` endpoint are stored on Amazon S3, it is necessary to pass the `--location` option to curl commands in order to allow curl to follow the redirect and retrieve the file. See the <a href='?shell#v2-datasets-group-dataset-forecast'>/v2/datasets/{group}/{dataset}/forecast/</a> section for more details.
</aside>

