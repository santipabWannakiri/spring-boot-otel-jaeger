<img width="1426" alt="exmaple-tracing" src="https://github.com/santipabWannakiri/spring-boot-otel-jaeger/assets/18206907/568e0007-f8a8-46bd-b069-b62dbcd26a83"># spring-boot-otel-jaeger
## Introduction
In contemporary software development, microservices architecture has emerged as a widely adopted approach. It offers benefits such as seamless scalability, fault isolation, and support for language-agnostic programming. However, the division of services into smaller units, each deployed in distinct environments, comes with its challenges. Coordinating services to collaborate in response to a client's action can be complex, especially when delays in one service can impact others. This raises important questions: How can we effectively monitor these services? How can we gain insights into the time each service consumes?

To address these inquiries, I delved into research to identify the common tools and frameworks used for tracing. Therefore, in this article, I will undertake a small POC to delve into the tracing of a microservice using OpenTelemetry and Jaeger.

## Tracing
<img src="images/example-tracing.png"  alt="image description" width="600" height="180">
tracing becomes crucial to understand how different services interact with each other to fulfill a user request. Tracing tools provide a detailed view of the end-to-end journey of a request, showing which services were involved, how much time each service took, and if there were any errors or delays.

## OpenTelemetry (OTEL)
is a versatile observability framework, providing APIs, libraries, and agents for streamlined instrumentation in cloud-native environments. Supporting multiple languages, it simplifies tracing, metrics, and logging, ensuring detailed performance data capture for effective monitoring and troubleshooting.\
In this scenario, we're going to focus on tracing only, and we will setup components for tracing at the following
>`OTEL Agent`: Streamlines the integration of OpenTelemetry instrumentation into applications, automating the collection and export of telemetry data, including traces and metrics.

>`OTEL Collector`: A versatile hub that receives, processes, and exports telemetry data. Configurable to support different input/output protocols, enhancing observability across various environments.


## Jaeger
Jaeger is an open-source distributed tracing system, part of the CNCF, designed to track transactions across microservices. With its user-friendly interface and compatibility with various backends, Jaeger visualizes and analyzes latency, making it a crucial tool for identifying bottlenecks and optimizing user experiences.


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
