# 🚀 Modern Full-Stack Monorepo Setup

A comprehensive TypeScript monorepo featuring React frontend, Fastify backend, and shared packages with modern development tools and deployment strategies.

## 🛠️ Tech Stack

![Node.js 20+](https://img.shields.io/badge/Node.js-20+-339933?style=flat&logo=node.js&logoColor=white)
![Yarn](https://img.shields.io/badge/Yarn-4.0+-2C8EBB?style=flat&logo=yarn&logoColor=white)
![React](https://img.shields.io/badge/React-18+-61DAFB?style=flat&logo=react&logoColor=black)
![Fastify](https://img.shields.io/badge/Fastify-4+-000000?style=flat&logo=fastify&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5+-3178C6?style=flat&logo=typescript&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-24+-2496ED?style=flat&logo=docker&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-7+-47A248?style=flat&logo=mongodb&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat&logo=vercel&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=flat&logo=swagger&logoColor=black)
![Storybook](https://img.shields.io/badge/Storybook-FF4785?style=flat&logo=storybook&logoColor=white)
![Jest](https://img.shields.io/badge/Jest/Vitest-C21325?style=flat&logo=jest&logoColor=white)
![Testcontainers](https://img.shields.io/badge/Testcontainers-40D09A?style=flat&logo=docker&logoColor=white)
![Husky](https://img.shields.io/badge/Husky-🐶-yellow?style=flat)

## 📦 Monorepo Architecture

### Project Structure

```
packages/
├── backend/              # Fastify API
│   ├── src/
│   │   ├── routes/       # user.route.ts, auth.route.ts
│   │   ├── services/     # user.service.ts
│   │   ├── repositories/ # user.repository.ts
│   │   ├── utils/        # date-helpers.util.ts
│   │   ├── plugins/      # Fastify plugins
│   │   ├── core/         # types, interfaces
│   │   └── __tests__/    # *.service.test.ts
├── frontend/             # React app
│   ├── src/
│   │   ├── components/   # UI components
│   │   ├── pages/        # Route pages
│   │   ├── hooks/        # Custom React hooks
│   │   ├── utils/        # Helper functions
│   │   ├── stores/       # State management
│   │   └── assets/       # Images, icons
└── shared/               # Common code
    ├── types/            # Shared TypeScript types
    ├── utils/            # Cross-platform utilities
    └── constants/        # Shared constants
```

### Key Features

- **Yarn Workspaces**: Efficient dependency management with shared node_modules and cross-package linking
- **Shared TypeScript**: Common types, interfaces, and utilities shared between client and server for consistency
- **Domain-driven Structure**: Clean separation of concerns with services, repositories, and clear architectural patterns
- **Fastify Performance**: High-performance backend with built-in validation, serialization, and plugin ecosystem
- **Testcontainers**: Real database testing with isolated Docker containers for reliable integration tests

## 🏗️ Naming Conventions

### Backend Patterns
```typescript
user.service.ts          # Business logic
user.service.test.ts     # Service tests
user.route.ts            # API endpoints
user.repository.ts       # Data access layer
auth.plugin.ts           # Fastify plugins
date-helpers.util.ts     # Utility functions
```

### Frontend Patterns
```typescript
UserProfile.tsx          # PascalCase components
useUserData.ts           # camelCase hooks
user-api.util.ts         # kebab-case utilities
```

## 🐳 Docker & Containerization

### Development Environment
- **Docker Compose**: Multi-service orchestration for development environment with MongoDB, API, and frontend
- **One-command Setup**: Complete development environment with hot reloading and service dependencies

```bash
# Start entire development stack
docker-compose up -d

# Install dependencies across monorepo
yarn install

# Services: mongodb, api, web, nginx
```

## 🌍 Environment Strategy

| Environment | Frontend | Backend | Database |
|-------------|----------|---------|----------|
| **Local** | Docker Compose | Docker Compose | MongoDB Container |
| **Development** | Vercel Preview | Fly.io Staging | MongoDB Atlas |
| **Production** | Vercel | Fly.io | MongoDB Atlas |

### Deployment Strategy
- **React Frontend**: Deployed on **Vercel** for blazing fast deployment with automatic previews and edge optimization
- **Fastify API**: Deployed on **Fly.io** for global deployment with built-in scaling and monitoring

## 🤖 Cursor Agent Configuration

AI-powered development with Cursor agent configured for TypeScript monorepo:

```json
{
  "typescript.preferences.useAliasesForRenames": true,
  "workbench.settings.editor": "json",
  "typescript.suggest.autoImports": true,
  "eslint.workingDirectories": ["packages/*"]
}
```

**Features**:
- Context-aware suggestions across packages
- Automated refactoring capabilities
- Intelligent code completion

## 🍃 MongoDB Integration

### Local Development
- MongoDB container in Docker Compose with persistent volumes
- Initialization scripts for development data

### Production
- **MongoDB Atlas** integration with connection pooling
- Automated backups and monitoring

```bash
# Environment variables
MONGODB_URI=mongodb://localhost:27017/myapp
MONGODB_ATLAS_URI=mongodb+srv://...
```

## 📖 API Documentation

### Swagger/OpenAPI Integration
- **Interactive API Documentation** with live testing capabilities
- **Automatic Schema Generation** from Fastify routes with `@fastify/swagger`
- **TypeScript Integration** ensuring consistency with shared types

```bash
# API Documentation endpoints
GET /docs           # Swagger UI interface
GET /docs/json      # OpenAPI specification

# Yarn workspace commands
yarn workspace backend add fastify
yarn workspace frontend add react
yarn workspace shared build
```

## 📚 Component Development

### Storybook Integration
- **Isolated Component Development** with interactive documentation
- **Design System** approach with centralized component library
- **Visual Testing** with Chromatic integration for automated UI review

```bash
# Storybook scripts
yarn storybook            # Start development server
yarn build-storybook     # Build static version
yarn test-storybook      # Run interaction tests
```

## 🧪 Testing Strategy

### Comprehensive Testing Approach

| Package | Framework | Purpose |
|---------|-----------|---------|
| **Frontend** | Vitest + React Testing Library | Component and integration testing |
| **Backend** | Node.js native test runner / Jest + Testcontainers | API endpoint and service testing with real databases |
| **Shared** | Jest/Vitest | Utility and type testing |
| **Storybook** | Play functions | Interactive component testing |
| **Integration** | Testcontainers | Database integration tests with Docker containers |

### Testcontainers Integration

**Real Database Testing** with isolated container instances:

```typescript
// backend/src/__tests__/user.integration.test.ts
import { GenericContainer } from 'testcontainers';
import { MongoDBContainer } from '@testcontainers/mongodb';

describe('User Integration Tests', () => {
  let mongoContainer: MongoDBContainer;
  let mongoUri: string;

  beforeAll(async () => {
    mongoContainer = await new MongoDBContainer('mongo:7')
      .withExposedPorts(27017)
      .start();
    
    mongoUri = mongoContainer.getConnectionString();
  });

  afterAll(async () => {
    await mongoContainer.stop();
  });

  it('should create user with real database', async () => {
    // Test with real MongoDB instance
  });
});
```

```bash
# Test scripts
yarn test                 # Run all tests
yarn test:watch          # Watch mode
yarn test:coverage       # Coverage reports
yarn test:integration    # Run integration tests with Testcontainers
yarn test-storybook      # Storybook interaction tests

# Workspace-specific testing
yarn workspace backend test
yarn workspace backend test:integration
yarn workspace frontend test
```

## ✨ Code Quality & Standards

### Automated Quality Checks

- **ESLint**: Shared linting rules across all packages with TypeScript support
- **Prettier**: Consistent code formatting with IDE integration
- **Husky**: Pre-commit hooks for automated quality enforcement

```bash
# .husky/pre-commit
#!/usr/bin/env sh
yarn lint-staged

# package.json
"lint-staged": {
  "*.{ts,tsx,js,jsx}": [
    "eslint --fix",
    "prettier --write",
    "yarn test --related --passWithNoTests"
  ],
  "*.{json,md}": [
    "prettier --write"
  ]
}
```

## 💡 Additional Recommendations

### Backend Enhancements
- **plugins/**: Fastify plugins for cross-cutting concerns
- **validators/**: Input validation schemas (Joi/Zod)
- **config/**: Environment-specific configurations
- **db/**: Database migrations, seeds, and setup
- **jobs/**: Background task handlers (queues, cron jobs)
- **hooks/**: Fastify lifecycle hooks

### Frontend Enhancements
- **stores/**: State management (Zustand, Redux Toolkit)
- **api/**: API client configuration and endpoint definitions
- **constants/**: Application-wide constants and enums
- **layouts/**: Reusable page layout components

### Shared Enhancements
- **schemas/**: Validation schemas shared between frontend/backend
- **enums/**: Shared enumerations and constants
- **fixtures/**: Test data, mocks, and sample data
- **docs/**: Architecture decisions, API docs, guides

### Development Tools
- **scripts/**: Build, deployment, and utility scripts
- **configs/**: Shared configurations for tools
- **templates/**: Code generation templates (Plop.js)
- **.vscode/**: Team editor settings and extensions

## 🎯 Key Benefits

### Developer Experience
- **Unified Development Environment** with shared tooling and consistent standards
- **Seamless Package Management** with Yarn workspaces
- **AI-Powered Development** with Cursor agent integration

### Scalability
- **Independent Deployment** of frontend and backend services
- **Optimized Hosting** solutions for each service type
- **Horizontal Scaling** capabilities with containerization

### Maintainability
- **Shared Types** prevent API contract mismatches
- **Consistent Linting** and formatting reduce technical debt
- **Comprehensive Testing** ensures code reliability

### Production Ready
- **Docker Containerization** ensures consistent environments
- **Automated CI/CD** with quality gates
- **Monitoring and Observability** built into deployment platforms

## 🚀 Getting Started

### Prerequisites
- Node.js 20+
- Yarn 4.0+
- Docker & Docker Compose

### Quick Start

```bash
# Clone the repository
git clone <repository-url>
cd <project-name>

# Install dependencies
yarn install

# Start development environment
docker-compose up -d

# Run the application
yarn dev
```

### Development Commands

```bash
# Install package in specific workspace
yarn workspace backend add fastify
yarn workspace frontend add react

# Run tests
yarn test
yarn workspace backend test
yarn workspace backend test:integration  # Run with Testcontainers
yarn workspace frontend test

# Build all packages
yarn build

# Start Storybook
yarn storybook

# Lint and format
yarn lint
yarn format
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

---

**Built with ❤️ using modern web technologies**