# spring-boot-otel-jaeger
## Introduction
In contemporary software development, microservices architecture has emerged as a widely adopted approach. It offers benefits such as seamless scalability, fault isolation, and support for language-agnostic programming. However, the division of services into smaller units, each deployed in distinct environments, comes with its challenges. Coordinating services to collaborate in response to a client's action can be complex, especially when delays in one service can impact others. This raises important questions: How can we effectively monitor these services? How can we gain insights into the time each service consumes?

To address these inquiries, I delved into research to identify the common tools and frameworks used for tracing. Therefore, in this article, I will undertake a small POC to delve into the tracing of a microservice using OpenTelemetry and Jaeger.

## Tracing

## OpenTelemetry

## Jaeger

ENVIRONMENT CONFIGURATION
(OpenTelemetry Protocol Exporter)[https://opentelemetry.io/docs/specs/otel/protocol/exporter/]

`export OTEL_METRICS_EXPORTER=none`

| Section   | Purpose                                                           | Example                                                                                                              |
|-----------|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Receivers | Configure receivers that listen for incoming data.               | - `otlp`: OTLP receiver for traces over gRPC.<br/> - `otlp/standalone`: OTLP receiver for metrics.<br/> - `zipkin`: Zipkin receiver for traces over HTTP.                       |
| Exporters | Configure exporters that send data to external systems.          | - `logging`: Logging Exporter for traces and metrics to the console. Useful for testing.                               |
| Processors| Configure processors that manipulate or transform data.          | - `batch`: Batch Processor to batch traces and metrics before exporting, reducing network overhead.                  |
| Extensions| Configure extensions providing additional functionality.          | - `health_check`: Health Check extension with a health check endpoint.<br/> - `zpages`: ZPages extension for web interface for debugging traces.                        |
| Service   | Define pipelines specifying how data flows through the collector.| - `pipelines`: Separate pipelines for traces, metrics, and logs.<br/> - `traces`: Trace pipeline with OTLP receiver and Logging Exporter.<br/> - `metrics`: Metrics pipeline with OTLP/standalone receiver and Logging Exporter.<br/> - `logs`: Logs pipeline with Zipkin receiver, Batch Processor, and Logging Exporter. |
