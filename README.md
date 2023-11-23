# spring-boot-otel-jaeger
POC project to explore solution for observation tools


### Receivers
- **Purpose:** Configure receivers that listen for incoming data from various sources.
- **Example:**
  - `otlp`: Configures the OTLP receiver to listen for traces over gRPC.
  - `otlp/standalone`: Configures another OTLP receiver for metrics independently.
  - `zipkin`: Configures the Zipkin receiver for traces over HTTP.

### Exporters
- **Purpose:** Configure exporters that send data to external systems or storage.
- **Example:**
  - `logging`: Configures the Logging Exporter to log traces and metrics to the console. Useful for testing and debugging.

### Processors
- **Purpose:** Configure processors that manipulate or transform data before export.
- **Example:**
  - `batch`: Configures the Batch Processor to batch traces and metrics before exporting, reducing network overhead.

### Extensions
- **Purpose:** Configure extensions that provide additional functionality to the collector.
- **Example:**
  - `health_check`: Configures the Health Check extension, adding a health check endpoint.
  - `zpages`: Configures the ZPages extension, providing a web interface for debugging traces.

### Service
- **Purpose:** Define pipelines specifying how data flows through the collector, connecting receivers, processors, and exporters.
- **Example:**
  - `pipelines`: Defines separate pipelines for traces, metrics, and logs.
  - `traces`: Configures a trace pipeline with the OTLP receiver and Logging Exporter.
  - `metrics`: Configures a metrics pipeline with the OTLP/standalone receiver and Logging Exporter.
  - `logs`: Configures a logs pipeline with the Zipkin receiver, Batch Processor, and Logging Exporter.
