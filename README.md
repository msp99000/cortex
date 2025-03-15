<img src="./assets/brain.svg" width="32" height="32" style="vertical-align: middle; margin-bottom: 4px;"> Cortex 

![Cortex](https://img.shields.io/badge/status-development-blue)
![License](https://img.shields.io/badge/license-MIT-green)

Cortex is a comprehensive knowledge management platform that leverages AI to transform how you store, retrieve, and interact with your information. With powerful local LLM integration, document processing, and intelligent search capabilities, Cortex helps you build a second brain for your data.

### Key Features

- **Document Intelligence**: Process, analyze, and extract insights from documents automatically
- **Semantic Search**: Find exactly what you need with natural language queries
- **Conversational AI**: Chat with your knowledge base using local LLMs
- **Multi-Agent Workflows**: Automated workflows for document analysis and knowledge extraction
- **Self-Hosted**: Complete privacy with fully local deployment

## Tech Stack

Cortex demonstrates advanced full-stack development with a modern AI-focused architecture:

| Component | Technologies |
|-----------|-------------|
| AI Backend | Python, Ollama, LangChain, LangGraph, LangSmith, FastAPI |
| Document Processing | Go, OCR, NLP |
| API Gateway | Node.js, Express |
| Frontend | TypeScript, React, TailwindCSS |
| Database | PostgreSQL with pgvector |
| DevOps | Docker, Kubernetes, GitHub Actions |

## Architecture

![Architecture Diagram](https://via.placeholder.com/800x400?text=Cortex+Architecture+Diagram)

Cortex employs a microservices architecture with the following components:

1. **Document Ingestion Service** (Go)
   - High-performance document processing
   - Metadata extraction and indexing
   - File type conversion and normalization

2. **AI Processing Engine** (Python)
   - RAG implementation with LangChain
   - Multi-agent coordination via LangGraph
   - Performance monitoring with LangSmith

3. **API Gateway** (Node.js)
   - Authentication and authorization
   - Request routing and service orchestration
   - Rate limiting and caching

4. **Frontend Application** (React/TypeScript)
   - Responsive document management interface
   - Interactive AI chat experience
   - Advanced search capabilities
   - Analytics dashboard

5. **Vector Database** (PostgreSQL/pgvector)
   - Embeddings storage and retrieval
   - Semantic search capabilities
   - Document metadata and user data

## Getting Started

### Prerequisites

- Docker and Docker Compose
- Kubernetes (minikube or k3s for local deployment)
- Git

### Local Development Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/cortex.git
   cd cortex
   ```

2. Start the development environment:
   ```bash
   docker-compose up -d
   ```

3. Access the application:
   ```
   Frontend: http://localhost:3000
   API Documentation: http://localhost:8000/docs
   ```

### Kubernetes Deployment

1. Build and push images (automated via GitHub Actions):
   ```bash
   kubectl apply -f k8s/
   ```

2. Access the deployed application:
   ```
   kubectl port-forward svc/cortex-frontend 3000:80
   ```

## Project Structure

```
cortex/
├── .github/
│   └── workflows/
│       ├── ci.yml                      # Continuous integration workflow
│       └── cd.yml                      # Continuous deployment workflow
│
├── api-gateway/                       # Node.js API Gateway
│   ├── src/
│   │   ├── controllers/               # Request handlers
│   │   ├── middleware/                # Authentication, logging, etc.
│   │   ├── routes/                    # API route definitions
│   │   ├── services/                  # Business logic
│   │   └── app.ts                     # Main application file
│   ├── tests/                         # API tests
│   ├── Dockerfile                     # Container definition
│   ├── package.json                   # Node dependencies
│   └── tsconfig.json                  # TypeScript configuration
│
├── document-service/                  # Go Document Processing Service
│   ├── cmd/
│   │   └── server/                    # Application entry point
│   ├── internal/
│   │   ├── api/                       # API handlers
│   │   ├── processor/                 # Document processing logic
│   │   ├── storage/                   # Storage interfaces
│   │   └── models/                    # Data models
│   ├── pkg/                           # Reusable packages
│   ├── tests/                         # Go tests
│   ├── Dockerfile                     # Container definition
│   └── go.mod                         # Go dependencies
│
├── ai-service/                        # Python AI Service
│   ├── app/
│   │   ├── api/                       # FastAPI routes
│   │   ├── core/                      # Core application logic
│   │   ├── models/                    # Data models
│   │   ├── services/
│   │   │   ├── langchain/            # LangChain implementations
│   │   │   ├── langgraph/            # LangGraph agent workflows
│   │   │   ├── vector_store/         # Vector database interactions
│   │   │   └── ollama/               # Ollama integration
│   │   └── main.py                    # Application entry point
│   ├── tests/                         # Python tests
│   ├── Dockerfile                     # Container definition
│   ├── requirements.txt               # Python dependencies
│   └── pyproject.toml                 # Python project metadata
│
├── frontend/                          # React/TypeScript Frontend
│   ├── public/                        # Static assets
│   ├── src/
│   │   ├── components/                # Reusable UI components
│   │   ├── contexts/                  # React contexts
│   │   ├── hooks/                     # Custom React hooks
│   │   ├── pages/                     # Application pages
│   │   ├── services/                  # API client services
│   │   ├── types/                     # TypeScript type definitions
│   │   ├── utils/                     # Utility functions
│   │   ├── App.tsx                    # Main App component
│   │   └── index.tsx                  # Application entry point
│   ├── tests/                         # Frontend tests
│   ├── Dockerfile                     # Container definition
│   ├── package.json                   # Frontend dependencies
│   ├── tsconfig.json                  # TypeScript configuration
│   └── vite.config.ts                 # Vite configuration
│
├── vector-db/                         # Chroma DB configuration
│   ├── config/                        # Chroma configuration
│   ├── persistence/                   # For persistent storage
│   └── Dockerfile                     # Chroma container definition
│
├── db/                                # Database configuration
│   ├── migrations/                    # SQL migrations
│   ├── init-scripts/                  # Database initialization scripts
│   └── Dockerfile                     # Database container definition
│
├── k8s/                               # Kubernetes configurations
│   ├── base/                          # Base configurations
│   │   ├── api-gateway.yaml
│   │   ├── document-service.yaml
│   │   ├── ai-service.yaml
│   │   ├── frontend.yaml
│   │   ├── chroma.yaml                # Chroma Deployment
│   │   └── postgres.yaml
│   ├── dev/                           # Development environment overrides
│   └── prod/                          # Production environment overrides
│
├── docker/                            # Docker configurations
│   ├── docker-compose.yml             # Local development compose
│   └── docker-compose.prod.yml        # Production compose configuration
│
├── scripts/                           # Utility scripts
│   ├── setup.sh                       # Development environment setup
│   └── seed-data.sh                   # Database seeding
│
├── docs/                              # Documentation
│   ├── architecture/                  # Architecture diagrams and docs
│   ├── api/                           # API documentation
│   └── user-guide/                    # End-user documentation
│
├── .gitignore                         # Git ignore file
├── README.md                          # Project README
└── LICENSE                            # Project license
```

## AI Features

- **RAG (Retrieval Augmented Generation)**: Enhance LLM responses with your knowledge base
- **Multi-Agent Systems**: Specialized AI agents collaborating on complex tasks
- **Document Understanding**: Extract structured data from unstructured documents
- **Knowledge Graphs**: Visualize connections between information
- **Conversational Memory**: Context-aware AI interactions

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [Ollama](https://github.com/ollama/ollama) for local LLM deployment
- [LangChain](https://github.com/langchain-ai/langchain) for RAG implementation
- [pgvector](https://github.com/pgvector/pgvector) for vector search capabilities
