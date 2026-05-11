# DemoService Documentation

## Overview

**DemoService** is a modern .NET Core microservice built with ASP.NET Core 8.0, designed to provide a RESTful API with comprehensive API documentation and Docker containerization support.

## Project Details

- **Framework**: .NET 8.0
- **Language**: C# (79.1%)
- **Containerization**: Docker (20.9%)
- **API Documentation**: Swagger/OpenAPI integrated

## Architecture

### Technology Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| Runtime | .NET | 8.0 |
| Web Framework | ASP.NET Core | 8.0 |
| API Documentation | Swagger/Swashbuckle | 6.6.2 |
| Containerization | Docker | - |
| IDE Support | Visual Studio | 17.14+ |

### Project Structure

```
DemoService/
├── DemoService.csproj          # Project configuration
├── Program.cs                  # Application entry point
├── Dockerfile                  # Docker containerization
└── [Controllers/]              # API controllers
```

## Features

- **RESTful API**: Full REST API implementation with standard HTTP methods
- **Swagger Integration**: Built-in API documentation and testing interface
- **Docker Support**: Multi-stage Docker build for optimized containerization
- **Security**: HTTPS redirection and authorization middleware configured
- **Modern C#**: Nullable reference types and implicit usings enabled

## Getting Started

### Prerequisites

- .NET 8.0 SDK or higher
- Docker (optional, for containerized deployment)
- Visual Studio 2022 or any compatible IDE

### Running Locally

Run the service using the .NET CLI:

```bash
dotnet run
```

The service will start and be accessible at `https://localhost:8081` (HTTPS) or `http://localhost:8080` (HTTP).

### Running with Docker

Build and run the Docker image:

```bash
# Build the Docker image
docker build -t demoservice:latest .

# Run the container
docker run -p 8080:8080 -p 8081:8081 demoservice:latest
```

The container exposes:
- **Port 8080**: HTTP endpoint
- **Port 8081**: HTTPS endpoint

## API Documentation

### Swagger/OpenAPI

When running in development mode, interactive API documentation is available at:

```
https://localhost:8081/swagger/ui
```

This provides:
- Complete API endpoint definitions
- Request/response schemas
- Live testing capabilities
- Authorization parameters (if configured)

### API Endpoints

All API endpoints are defined in the project's controllers. Access the Swagger UI for a complete, up-to-date list of available endpoints.

## Configuration

### Application Settings

Configuration is managed through standard .NET configuration providers:

- `appsettings.json` - Default configuration
- `appsettings.Development.json` - Development-specific overrides
- User Secrets (for local development sensitive data)
  - User Secrets ID: `62dadd4b-a2df-4ff5-8d89-50d4dcd7b0b1`

### Build Configurations

The solution supports multiple configurations:

- **Debug**: Development build with debugging support
- **Release**: Optimized production build

## Development

### Building the Project

```bash
# Debug build
dotnet build -c Debug

# Release build
dotnet build -c Release
```

### Project Configuration

The project enables modern C# features:

- **Nullable reference types**: `<Nullable>enable</Nullable>`
- **Implicit usings**: `<ImplicitUsings>enable</ImplicitUsings>`
- **ASP.NET Core Web SDK**: Included via `Microsoft.NET.Sdk.Web`

### Dependencies

```xml
Microsoft.VisualStudio.Azure.Containers.Tools.Targets (v1.22.1)
Swashbuckle.AspNetCore (v6.6.2)
```

## Deployment

### Docker Deployment

The project includes a multi-stage Dockerfile optimized for production:

1. **Base Stage**: Runtime environment (mcr.microsoft.com/dotnet/aspnet:8.0)
2. **Build Stage**: Compilation environment (mcr.microsoft.com/dotnet/sdk:8.0)
3. **Publish Stage**: Application publication
4. **Final Stage**: Production-ready image

### Environment Variables

Set environment variables for different deployments:

- `ASPNETCORE_ENVIRONMENT`: Set to `Production` for production deployments

## Middleware Pipeline

The application is configured with the following middleware (in order):

1. **Swagger** (Development only)
2. **HTTPS Redirection**
3. **Authorization**
4. **Controller Routing**

## Security Features

- ✅ HTTPS redirection enforced
- ✅ Authorization middleware configured
- ✅ Nullable reference types enabled for type safety
- ⚙️ API authentication can be configured via User Secrets

## Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| Port already in use | Change the port in `launchSettings.json` or run on different port |
| SSL/TLS certificate error | Ensure HTTPS development certificate is installed: `dotnet dev-certs https --trust` |
| Docker build fails | Verify .NET SDK version matches Dockerfile `FROM mcr.microsoft.com/dotnet/sdk:8.0` |

### Useful Commands

```bash
# Install development HTTPS certificate
dotnet dev-certs https --trust

# Clean build
dotnet clean
dotnet build

# Run tests (if test projects exist)
dotnet test

# Publish for deployment
dotnet publish -c Release -o ./publish
```

## Solution Structure

The solution file (`DemoService.sln`) contains:

- **Project**: DemoService (GUID: EFD63155-C2A7-4EC4-9598-A3E05E8D1D1D)
- **Configurations**: Debug and Release for Any CPU platform

## Monitoring & Logging

ASP.NET Core provides built-in logging:

```csharp
// Logs are output to the console by default
// Configure additional providers in Program.cs
```

## Contributing

When contributing to this project:

1. Follow C# coding standards and conventions
2. Enable and respect nullable reference types
3. Maintain API backward compatibility
4. Update Swagger documentation for new endpoints
5. Test locally before submitting changes

## References

- [ASP.NET Core Documentation](https://docs.microsoft.com/aspnet/core)
- [Swagger/OpenAPI Documentation](https://swagger.io)
- [Docker Documentation](https://docs.docker.com)
- [.NET 8.0 Release Notes](https://docs.microsoft.com/dotnet/core/whats-new/dotnet-8)

## Support

For issues or questions:

1. Check Swagger UI for endpoint documentation
2. Review application logs in the console output
3. Consult the troubleshooting section above
4. Open an issue on the project repository
