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
![Redis](https://img.shields.io/badge/Redis-7+-DC382D?style=flat&logo=redis&logoColor=white)
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
- **Redis Caching**: High-performance in-memory caching for sessions, API responses, and frequently accessed data
- **Testcontainers**: Real database testing with isolated Docker containers for reliable integration tests

## 🏗️ Naming Conventions

### Backend Patterns

```typescript
user.service.ts          # Business logic
user.service.test.ts     # Service tests
user.route.ts            # API endpoints
user.repository.ts       # Data access layer
user.cache.ts            # Redis caching layer
auth.plugin.ts           # Fastify plugins
cache.plugin.ts          # Redis plugin
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

# Services: mongodb, redis, api, web, nginx
```

## 🌍 Environment Strategy

| Environment     | Frontend       | Backend        | Database          | Cache           |
| --------------- | -------------- | -------------- | ----------------- | --------------- |
| **Local**       | Docker Compose | Docker Compose | MongoDB Container | Redis Container |
| **Development** | Vercel Preview | Fly.io Staging | MongoDB Atlas     | Redis Cloud     |
| **Production**  | Vercel         | Fly.io         | MongoDB Atlas     | Redis Cloud     |

### Deployment Strategy

- **React Frontend**: Deployed on **Vercel** for blazing fast deployment with automatic previews and edge optimization
- **Fastify API**: Deployed on **Fly.io** for global deployment with built-in scaling and monitoring

## ⚡ Redis Caching

### High-Performance In-Memory Caching

- **Session Management**: User sessions, authentication tokens, and temporary data
- **API Response Caching**: Frequently requested data with configurable TTL
- **Database Query Optimization**: Cache expensive database operations
- **Rate Limiting**: API throttling and request counting

### Local Development

- Redis container in Docker Compose with persistent volumes
- Redis Commander web UI for cache inspection and debugging

### Production

- **Redis Cloud** integration with clustering and high availability
- Automated failover and monitoring

```bash
# Environment variables
REDIS_URL=redis://localhost:6379
REDIS_CLOUD_URL=redis://username:password@host:port

# Redis integration example
import Redis from 'ioredis';
const redis = new Redis(process.env.REDIS_URL);

// Cache user session
await redis.setex(`session:${userId}`, 3600, JSON.stringify(session));

// Cache API response
await redis.setex(`api:users:${page}`, 300, JSON.stringify(users));
```

## 🤖 Cursor Agent Configuration

AI-powered development with Cursor agent configured for TypeScript monorepo:

```json
{
  "typescript.preferences.useAliasesForRenames": true,
  "workbench.settings.editor": "json",
  "typescript.suggest.autoImports": true,
  "eslint.workingDirectories": ["packages/*"],
  "cursor.ai.enableCodeCompletion": true,
  "cursor.ai.enableInlineChat": true,
  "cursor.ai.modelPreference": "claude-3.5-sonnet"
}
```

### Advanced Cursor Usage Patterns

**🎯 Monorepo-Aware Development**:

- **Cross-Package Refactoring**: AI understands package dependencies and suggests safe refactors across the entire monorepo
- **Type-Safe Code Generation**: Leverages shared types to generate consistent code between frontend and backend
- **Smart Import Management**: Automatically handles complex import paths between packages

**🔧 Development Workflows**:

```bash
# AI-Assisted Feature Development
# 1. Describe feature in natural language
# 2. Cursor generates:
#    - Backend API route with validation
#    - Frontend component with proper types
#    - Shared types and interfaces
#    - Test files with realistic test cases

# Example Cursor prompts:
"Create a user profile update feature with validation"
"Add Redis caching to the user service with 1 hour TTL"
"Generate integration tests for the authentication flow"
```

**🧠 Intelligent Code Assistance**:

- **Context-Aware Suggestions**: Understands Fastify patterns, React hooks, and MongoDB schemas
- **Error Resolution**: Provides specific fixes for TypeScript errors across packages
- **Performance Optimization**: Suggests Redis caching opportunities and database query improvements
- **Security Best Practices**: Identifies and fixes security vulnerabilities automatically

**📝 Documentation Generation**:

- **API Documentation**: Auto-generates Swagger/OpenAPI specs from Fastify routes
- **Component Stories**: Creates Storybook stories for React components
- **README Updates**: Maintains project documentation as code evolves

**🔍 Code Analysis & Refactoring**:

- **Dependency Analysis**: Visualizes package relationships and suggests optimizations
- **Dead Code Detection**: Identifies unused code across the monorepo
- **Architecture Validation**: Ensures code follows established patterns and conventions

### Cursor Agent Features:

- **Context-aware suggestions** across packages with deep understanding of monorepo structure
- **Automated refactoring capabilities** that respect package boundaries and shared dependencies
- **Intelligent code completion** with TypeScript integration and shared type awareness
- **Natural language code generation** for complex features spanning multiple packages
- **Real-time error detection** and resolution suggestions with package-specific context

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
REDIS_URL=redis://localhost:6379
REDIS_CLOUD_URL=redis://username:password@host:port
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
yarn workspace backend add ioredis @types/ioredis
yarn workspace frontend add react
yarn workspace shared build

# Redis commands
yarn workspace backend add ioredis @types/ioredis  # Redis client
yarn workspace backend add redis-commander         # Redis web UI
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

| Package         | Framework                                          | Purpose                                                     |
| --------------- | -------------------------------------------------- | ----------------------------------------------------------- |
| **Frontend**    | Vitest + React Testing Library                     | Component and integration testing                           |
| **Backend**     | Node.js native test runner / Jest + Testcontainers | API endpoint and service testing with real databases        |
| **Shared**      | Jest/Vitest                                        | Utility and type testing                                    |
| **Storybook**   | Play functions                                     | Interactive component testing                               |
| **Integration** | Testcontainers                                     | Database and Redis integration tests with Docker containers |
| **Cache**       | Testcontainers + Redis                             | Redis caching logic testing with isolated containers        |

### Testcontainers Integration

**Real Database Testing** with isolated container instances:

```typescript
// backend/src/__tests__/user.integration.test.ts
import { GenericContainer } from "testcontainers";
import { MongoDBContainer } from "@testcontainers/mongodb";
import { RedisContainer } from "@testcontainers/redis";

describe("User Integration Tests", () => {
  let mongoContainer: MongoDBContainer;
  let redisContainer: RedisContainer;
  let mongoUri: string;
  let redisUrl: string;

  beforeAll(async () => {
    // Start MongoDB container
    mongoContainer = await new MongoDBContainer("mongo:7")
      .withExposedPorts(27017)
      .start();

    // Start Redis container
    redisContainer = await new RedisContainer("redis:7-alpine")
      .withExposedPorts(6379)
      .start();

    mongoUri = mongoContainer.getConnectionString();
    redisUrl = `redis://${redisContainer.getHost()}:${redisContainer.getMappedPort(
      6379
    )}`;
  });

  afterAll(async () => {
    await Promise.all([mongoContainer.stop(), redisContainer.stop()]);
  });

  it("should create user with real database and cache", async () => {
    // Test with real MongoDB and Redis instances
    // Verify data persistence and cache invalidation
  });

  it("should cache user data in Redis", async () => {
    // Test Redis caching functionality
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
- **cache/**: Redis caching strategies and implementations
- **validators/**: Input validation schemas (Joi/Zod)
- **config/**: Environment-specific configurations
- **db/**: Database migrations, seeds, and setup
- **jobs/**: Background task handlers (queues, cron jobs)
- **hooks/**: Fastify lifecycle hooks
- **middleware/**: Request/response middleware including cache headers

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

# Redis development
docker exec -it redis-container redis-cli  # Access Redis CLI
yarn workspace backend redis:flush         # Clear Redis cache
yarn workspace backend redis:monitor       # Monitor Redis commands
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

---

**Built with ❤️ using modern web technologies**
