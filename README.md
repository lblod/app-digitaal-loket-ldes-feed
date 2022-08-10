# app-lpdc-ldes-feed
This application is meant to host ldes-streams relevant in the context of the IPDC-LPDC project.
In the future we might transfer these ldes-streams to another app (e.g. app-centrale-vindplaats). But extended preparation is required for this.
Now, we need to get the ball rolling and get experience with ldes. Hence the separate app.

⚠ ️Note: This is not a standard semantic.works stack.
- This application does not host the expected services such as mu-identifier, mu-dispatcher, etc..., as only one endpoint is exposed.
- Services call each other. (cf. infra)

This app is meant to be a throw-away app;
  - once Informatie Vlaanderen can independently consume `ldes:EventStream` and,
  - we moved the stream to app-centrale-vindplaats

we will tear it down again.

## overview of the services
### fragmentation-producer
This service provides an endpoint where users can query LDES streams or add versioned members to a stream using HTTP.
See [redpencilio/fragmentation-producer-service](https://github.com/redpencilio/fragmentation-producer-service)

### ipdc-ldes-consumer
Temporary service to help informatie vlaanderen get started with our data and ldes.
The service pulls data from fragmentation-producer and publishes the new information to an external endpoint provided by Informatie Vlaanderen as `JSON-LD`

## Running
### Running the regular setup

```
docker-compose up
```
### Running the dev setup
```
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up
```
