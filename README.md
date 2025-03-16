# TruthStory Project

## Project Overview
TruthStory is a SaaS platform designed to provide comprehensive media and news analysis. The platform leverages advanced technologies including web crawling, artificial intelligence, and knowledge graphs to deliver deep insights into news content, its authenticity, and propagation patterns.

### Core Services

1. **News Crawler Service**
   - Automated news content collection
   - Data storage and management
   - Real-time content monitoring

2. **AI Analysis & Knowledge Graph Service**
   - Content analysis using artificial intelligence
   - Knowledge graph construction to map relationships between:
     - Media sources
     - People
     - Organizations
     - Facts
     - Events
     - Opinions
   - Pattern recognition and relationship mapping

3. **Fake News Detection Service**
   - Automated fact-checking
   - Source credibility analysis
   - Content verification algorithms

4. **News Propagation Analysis Service**
   - Track information spread patterns
   - Identify key propagation channels
   - Measure impact and reach
   - Timeline analysis

5. **User Interface**
   - Interactive visualization of analyzed data
   - Knowledge graph exploration
   - Real-time analytics dashboard
   - Search and filtering capabilities

6. **Demo Interface**
   - Lightweight testing environment for services
   - Direct service integration testing
   - Pre-defined test scenarios
   - No code duplication - uses actual service endpoints
   - Features:
     - Individual service testing
     - Multi-service integration testing
     - Quick demo capabilities
     - API documentation and examples

## Development Context

### Project Structure
The project follows a microservices architecture with the following structure:

```
truthstory/
├── specifications/         # Comprehensive service specifications
│   ├── services/          # Individual service specifications
│   ├── interfaces/        # Interface and API specifications
│   ├── architecture/      # System architecture specifications
│   └── data-models/       # Data structure specifications
├── services/
│   ├── news-crawler/      # News crawling and storage service
│   ├── knowledge-graph/   # AI analysis and knowledge graph service
│   ├── fake-news-detector/# Fake news detection service
│   ├── news-propagation/ # News propagation analysis service
│   └── ui/               # User interface application
├── demo-interface/        # Testing interface for services
│   ├── scenarios/        # Pre-defined test scenarios
│   ├── api/              # Simple API gateway for testing
│   └── web/              # Minimal web interface for demos
├── shared/               # Shared libraries and utilities
├── docs/                 # Project documentation
└── deploy/               # Deployment configurations
```

Each service is designed to be independently deployable and maintainable, while sharing common infrastructure and communication protocols.

### Development Rules

1. Specification-First Development
   - All features must be specified in `/specifications` before implementation
   - Specifications must be reviewed and approved
   - Implementation must follow approved specifications
   - Any deviations from specs require documentation and approval

2. External Services and APIs
   - Never use any external APIs or services unless explicitly approved
   - Maintain a list of approved external services in the project documentation
   - All external integrations must be reviewed and documented

2. Code Quality
   - Write clean, efficient code with minimal but meaningful comments
   - Focus on making minimal necessary changes
   - Split large functions/files when appropriate
   - Follow consistent coding style

3. Testing
   - Implement tests for new features
   - Create tests to verify bug fixes
   - Follow test-driven development when appropriate

4. Version Control
   - Make atomic commits with clear messages
   - Branch for features/fixes
   - Review changes before committing

### Environment Setup
- Development server ports:
  - Primary port: 53028
  - Secondary port: 57585
- Server Configuration:
  - Allow iframes
  - Enable CORS requests
  - Allow access from any host (0.0.0.0)

### Progress Tracking

#### Completed Tasks
- Initial repository setup
- Created development context documentation

#### Pending Tasks
- [To be added as tasks are defined]

### Technical Specifications

#### Architecture Overview
- Microservices-based architecture
- Event-driven communication between services
- RESTful APIs for service interfaces
- Containerized deployment

#### Technology Stack
- **Backend Services**: Python-based microservices
- **Data Storage**:
  - Document store for news articles
  - Graph database for knowledge representation
  - Time-series database for analytics
- **Message Queue**: For event-driven communication
- **Frontend**: Modern web application
- **Infrastructure**: Container orchestration

#### Service Communication
- REST APIs for synchronous operations
- Event-based messaging for asynchronous operations
- Shared data formats and protocols
- Service discovery and health monitoring

#### Demo Interface Architecture
- **API Gateway**:
  - Lightweight proxy to service endpoints
  - Request/response logging
  - Error handling and visualization
  - Rate limiting for testing

- **Test Scenarios**:
  - YAML-defined test flows
  - Service integration patterns
  - Mock data generators
  - Scenario replay capabilities

- **Web Interface**:
  - Simple, dependency-free UI
  - Direct service interaction
  - Real-time response visualization
  - Swagger/OpenAPI documentation integration

### Approved External Services and APIs
This is a comprehensive list of external services and APIs that have been explicitly approved for use in this project:
- [None approved yet]

### Notes
- This is a new repository that will be built from scratch
- Development will follow best practices and maintain clear documentation