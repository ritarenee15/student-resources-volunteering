# New Relic for Students Resources Build

## Overview
Your task for today will be building an interactive resource for New Relic for Students participants. This resource will live on the [New Relic for Students Resources Page](https://newrelic.com/students/resources), where students will be able to learn more about observability and New Relic using hands-on tutorials.

## The Task
For today's task, you'll be broken up into groups of two or three, and will be assigned to create a resource for one of the four telemetry data types - metrics, events, logs, or traces. Within your groups, you'll create a resource that will help users understand these data types, and how New Relic will help them understand the data coming from their applications and how it can be used to help them solve and eliminate disruptions.

You'll create a repository for your group. Each repository should, at a minimum, have the following information in the README:
- Overview of the data type (what it is, why it's used)
- Information on how it's used in New Relic
- Images or video on how to view it in New Relic
- Tasks that the student can complete to show understanding of the material
- Resources for further learning

This resource can be anything, from a written doc to an interactive tutorial. Whatever feels comfortable for you and your group to present this information works. This is meant to be a fun activity, and as students, you have a unique point of view that can help fellow students understand why observability should be a part of their toolkit.

## Resources
- [New Relic Docs](https://docs.newrelic.com/)
- [New Relic Blog](https://newrelic.com/blog)

## Sample Applications
- [OpenTelemetry Demo App](https://github.com/open-telemetry/opentelemetry-demo)
  If you want to utilize the demo app, you can instrument it with New Relic by pasting this in the `otel-config-extras.yml` file:
```
# SPDX-License-Identifier: Apache-2.0

# extra settings to be merged into OpenTelemetry Collector configuration
# do not delete this file

## Example configuration for sending data to your own OTLP HTTP backend
## Note: the spanmetrics exporter must be included in the exporters array
## if overriding the traces pipeline.
##
#  exporters:
#    otlphttp/example:
#      endpoint: <your-endpoint-url>
#
#  service:
#    pipelines:
#      traces:
#        exporters: [spanmetrics, otlphttp/example]
exporters:
  otlp/newrelic:
    endpoint: https://otlp.nr-data.net:4317
    headers:
      api-key: #New Relic License Key Here

service:
  pipelines:
    traces:
      receivers: [otlp]
      processors: [batch]
      exporters: [otlp/newrelic]
    metrics:
      receivers: [otlp]
      processors: [batch]
      exporters: [otlp/newrelic]
    logs:
      receivers: [otlp]
      processors: [batch]
      exporters: [otlp/newrelic]

```
- [Docker Sample Voting App](https://github.com/dockersamples/example-voting-app)

## Groups
- Metrics: Klinton, Kyle, Yashashree
- Events: Justin, Luis
- Logs: Bella, Amy
- Traces: Tommy, Emily, Seline
