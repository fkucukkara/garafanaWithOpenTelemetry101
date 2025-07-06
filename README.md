# OpenTelemetry with Grafana Integration Example

This project demonstrates the integration of OpenTelemetry with Grafana in a .NET API application. It serves as a practical example of implementing observability in a modern .NET application using OpenTelemetry for telemetry data collection and Grafana for visualization.

## 🚀 Project Overview

This is a sample Weather Forecast API that implements OpenTelemetry instrumentation to collect metrics, traces, and logs, which are then exported to Grafana Cloud using the OTLP (OpenTelemetry Protocol) exporter.

## 📋 Prerequisites

- .NET 9.0 SDK
- Grafana Cloud Account
- Basic understanding of OpenTelemetry concepts

## 🔧 Technology Stack

- **.NET 9.0**: The core framework
- **OpenTelemetry**: For telemetry data collection
- **Grafana Cloud**: For data visualization and analysis
- **OTLP Exporter**: For sending telemetry data to Grafana

## 🎯 Features

- Complete OpenTelemetry integration
- Automatic instrumentation for:
  - ASP.NET Core
  - HTTP clients
  - Runtime metrics
  - Process metrics
- Structured logging with OpenTelemetry
- Trace context propagation
- Custom attribute addition

## 📦 OpenTelemetry Components Used

The project uses the following OpenTelemetry components:

1. **Resource Configuration**:
   ```csharp
   .ConfigureResource(resource =>
   {
       resource
           .AddService(serviceName: "GrafanaPlayground", serviceVersion: "1.0.0")
           .AddAttributes([
               new("deployment.environment", builder.Environment.EnvironmentName)
           ]);
   })
   ```

2. **Metrics Configuration**:
   - AspNetCore instrumentation
   - HttpClient instrumentation
   - Runtime metrics
   - Process metrics

3. **Tracing Configuration**:
   - AspNetCore instrumentation
   - HttpClient instrumentation

4. **Logging Configuration**:
   - Formatted messages
   - Logging scopes
   - State value parsing

## 🔌 Grafana Integration

### Configuration
The project is configured to export telemetry data to Grafana Cloud using the OTLP exporter. The configuration is done through environment variables:

```plaintext
OTEL_EXPORTER_OTLP_PROTOCOL=http/protobuf
OTEL_EXPORTER_OTLP_ENDPOINT=https://otlp-gateway-prod-eu-west-2.grafana.net/otlp
OTEL_EXPORTER_OTLP_HEADERS=Authorization=Basic [Your-Auth-Token]
```

### Data Types Exported
1. **Metrics**:
   - Request counts and durations
   - Runtime metrics (GC, thread pool, etc.)
   - Process metrics (CPU, memory, etc.)

2. **Traces**:
   - HTTP request traces
   - Internal operation traces
   - Cross-cutting concern traces

3. **Logs**:
   - Structured application logs
   - Request logs
   - System logs

## 🚦 Getting Started

1. Clone the repository
2. Configure your Grafana Cloud credentials in `launchSettings.json`
3. Run the application:
   ```bash
   dotnet run
   ```
4. Access the API at `http://localhost:5058/weatherforecast`

## 📊 Viewing Telemetry Data in Grafana

1. Log into your Grafana Cloud account
2. Navigate to Explore
3. Select the appropriate data source:
   - Tempo for traces
   - Prometheus for metrics
   - Loki for logs

## 🔍 Available Endpoints

- `GET /weatherforecast`: Returns a 5-day weather forecast
  - Includes OpenTelemetry instrumentation
  - Logs request information
  - Generates traces and metrics

## 🛠️ OpenTelemetry Best Practices Implemented

1. **Service Name and Version**:
   - Clear service identification
   - Version tracking for deployment monitoring

2. **Environment Attributes**:
   - Environment-specific tracking
   - Deployment context preservation

3. **Comprehensive Instrumentation**:
   - Multiple instrumentation types
   - Complete system observability

4. **Structured Logging**:
   - Consistent log formatting
   - Context preservation
   - Correlation with traces

## 📈 Monitoring in Grafana

### Available Metrics
- Request counts and latencies
- Runtime performance metrics
- Process resource utilization
- Custom business metrics

### Available Traces
- End-to-end request traces
- Internal operation spans
- Cross-service communication

### Available Logs
- Application logs
- Request/Response logs
- System events

## 🤝 Contributing

Feel free to contribute to this project by submitting issues or pull requests.

## License
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

This project is licensed under the MIT License, which allows you to freely use, modify, and distribute the code. See the [`LICENSE`](LICENSE) file for full details.

## 🔗 Resources

- [OpenTelemetry Documentation](https://opentelemetry.io/docs/)
- [Grafana Documentation](https://grafana.com/docs/)
- [OpenTelemetry .NET SDK](https://github.com/open-telemetry/opentelemetry-dotnet)
- [Grafana Cloud](https://grafana.com/products/cloud/)
