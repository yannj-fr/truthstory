# Demo Interface

## Overview
The Demo Interface provides a lightweight testing environment for TruthStory services. It enables direct testing of individual services and multi-service integrations without duplicating any service code.

## Key Principles
1. **No Code Duplication**: All tests use actual service endpoints
2. **Lightweight**: Minimal dependencies, simple setup
3. **Comprehensive Testing**: Support for both individual and integrated service testing
4. **Clear Documentation**: Every endpoint and scenario is well-documented

## Components

### 1. API Gateway (`/api`)
- Proxies requests to actual services
- Provides unified logging and monitoring
- Handles error visualization
- Implements testing rate limits

### 2. Test Scenarios (`/scenarios`)
- YAML-defined test flows
- Integration patterns
- Mock data definitions
- Scenario replay configurations

### 3. Web Interface (`/web`)
- Simple HTML/JS interface
- Direct service interaction
- Real-time response display
- OpenAPI documentation

## Usage

### Running Individual Service Tests
```bash
# Example commands will be added
```

### Running Integration Tests
```bash
# Example commands will be added
```

### Adding New Test Scenarios
1. Create a new YAML file in `/scenarios`
2. Define test flow and expected results
3. Add any required mock data
4. Document the scenario

## Development Guidelines

### Adding New Features
1. No service logic in demo interface
2. Use service APIs directly
3. Keep dependencies minimal
4. Document all additions

### Testing
1. Verify with actual services
2. Test error handling
3. Validate documentation
4. Check performance impact