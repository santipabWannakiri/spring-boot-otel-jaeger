# spring-boot-otel-jaeger
POC project to explore solution for observation tools


| Section   | Purpose                                                           | Example                                                                                                              |
|-----------|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Receivers | Configure receivers that listen for incoming data.               | - `otlp`: OTLP receiver for traces over gRPC.<br/> - `otlp/standalone`: OTLP receiver for metrics.<br/> - `zipkin`: Zipkin receiver for traces over HTTP.                       |
| Exporters | Configure exporters that send data to external systems.          | - `logging`: Logging Exporter for traces and metrics to the console. Useful for testing.                               |
| Processors| Configure processors that manipulate or transform data.          | - `batch`: Batch Processor to batch traces and metrics before exporting, reducing network overhead.                  |
| Extensions| Configure extensions providing additional functionality.          | - `health_check`: Health Check extension with a health check endpoint.<br/> - `zpages`: ZPages extension for web interface for debugging traces.                        |
| Service   | Define pipelines specifying how data flows through the collector.| - `pipelines`: Separate pipelines for traces, metrics, and logs.<br/> - `traces`: Trace pipeline with OTLP receiver and Logging Exporter.<br/> - `metrics`: Metrics pipeline with OTLP/standalone receiver and Logging Exporter.<br/> - `logs`: Logs pipeline with Zipkin receiver, Batch Processor, and Logging Exporter. |
