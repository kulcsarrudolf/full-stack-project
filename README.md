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
![Auth0](https://img.shields.io/badge/Auth0-000000?style=flat&logo=auth0&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-06B6D4?style=flat&logo=tailwindcss&logoColor=white)
![Resend](https://img.shields.io/badge/Resend-000000?style=flat&logo=resend&logoColor=white)
![Twilio](https://img.shields.io/badge/Twilio-000000?style=flat&logo=twilio&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)

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
├── external-services/    # Third-party integrations
│   ├── src/
│   │   ├── providers/    # payment.provider.ts, email.provider.ts, sms.provider.ts, auth.provider.ts
│   │   ├── clients/      # stripe.client.ts, resend.client.ts, twilio.client.ts, auth0.client.ts
│   │   ├── webhooks/     # stripe.webhook.ts, resend.webhook.ts, twilio.webhook.ts
│   │   ├── adapters/     # External API adapters
│   │   ├── schemas/      # External service schemas
│   │   ├── utils/        # Service-specific utilities
│   │   └── __tests__/    # External service tests
├── mcp-mongo-server/    # MCP server for MongoDB operations
│   ├── src/
│   │   ├── tools/        # MCP tools for database operations
│   │   ├── middleware/   # Authorization and validation middleware
│   │   ├── types/        # MCP-specific TypeScript types
│   │   ├── utils/        # MongoDB utilities and helpers
│   │   ├── server.ts     # MCP server entry point
│   │   └── __tests__/    # MCP server tests
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

### External Services Patterns

```typescript
stripe.provider.ts       # Payment provider
resend.client.ts         # Email service client
twilio.client.ts         # SMS service client
auth0.client.ts          # Auth0 authentication client
auth0-management.client.ts # Auth0 Management API client
github.webhook.ts        # Webhook handlers
slack.adapter.ts         # API adapters
payment.schema.ts        # Service schemas
email.schema.ts          # Email validation schemas
sms.schema.ts            # SMS validation schemas
auth.schema.ts           # Authentication schemas
webhook.util.ts          # Utility functions
stripe.test.ts           # Service tests
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

// External services integration example
import { Resend } from 'resend';
import { Twilio } from 'twilio';

const resend = new Resend(process.env.RESEND_API_KEY);
const twilio = new Twilio(process.env.TWILIO_ACCOUNT_SID, process.env.TWILIO_AUTH_TOKEN);

// Send welcome email
await resend.emails.send({
  from: 'onboarding@app.com',
  to: ['user@example.com'],
  subject: 'Welcome to our platform!',
  react: WelcomeEmailTemplate({ name: 'John' })
});

// Send SMS verification
await twilio.messages.create({
  body: `Your verification code is: ${code}`,
  from: process.env.TWILIO_PHONE_NUMBER,
  to: '+1234567890'
});
```

## 🤖 MCP MongoDB Server

### Enterprise-Grade Database Operations with Authorization

**🎯 Why MCP Server for MongoDB Operations:**

✅ **Secure Database Access**: Role-based authorization for all database operations  
✅ **Type-Safe Operations**: TypeScript integration with MongoDB schemas  
✅ **Input Validation**: Comprehensive query sanitization and validation  
✅ **Audit Logging**: Complete operation tracking and security logging  
✅ **Rate Limiting**: Built-in protection against database abuse  
✅ **Connection Pooling**: Efficient MongoDB connection management  
✅ **Error Handling**: Robust error handling with detailed logging

### MCP Server Architecture

**Complete MongoDB operations server with authorization:**

```typescript
// mcp-mongo-server/src/server.ts
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import {
  CallToolRequestSchema,
  ListToolsRequestSchema,
} from "@modelcontextprotocol/sdk/types.js";
import { MongoClient, Db } from "mongodb";
import { AuthMiddleware } from "./middleware/auth.middleware.js";
import { ValidationMiddleware } from "./middleware/validation.middleware.js";
import { MongoTools } from "./tools/mongo.tools.js";

export class MCPMongoServer {
  private server: Server;
  private db: Db;
  private authMiddleware: AuthMiddleware;
  private validationMiddleware: ValidationMiddleware;
  private mongoTools: MongoTools;

  constructor() {
    this.server = new Server(
      {
        name: "mcp-mongo-server",
        version: "1.0.0",
      },
      {
        capabilities: {
          tools: {},
          logging: {},
        },
      }
    );

    this.authMiddleware = new AuthMiddleware();
    this.validationMiddleware = new ValidationMiddleware();
    this.setupHandlers();
  }

  async initialize() {
    // Connect to MongoDB
    const client = new MongoClient(process.env.MONGODB_URI!);
    await client.connect();
    this.db = client.db(process.env.MONGODB_DATABASE || "myapp");

    this.mongoTools = new MongoTools(this.db);

    // Start server
    const transport = new StdioServerTransport();
    await this.server.connect(transport);
  }

  private setupHandlers() {
    this.server.setRequestHandler(ListToolsRequestSchema, async () => ({
      tools: [
        {
          name: "mongo_find",
          description:
            "Find documents in MongoDB collection with authorization",
          inputSchema: {
            type: "object",
            properties: {
              collection: { type: "string", description: "Collection name" },
              filter: { type: "object", description: "MongoDB filter query" },
              options: {
                type: "object",
                description: "Query options (limit, sort, etc.)",
              },
              auth_token: {
                type: "string",
                description: "Authorization token",
              },
            },
            required: ["collection", "filter", "auth_token"],
          },
        },
        {
          name: "mongo_insert",
          description:
            "Insert documents into MongoDB collection with authorization",
          inputSchema: {
            type: "object",
            properties: {
              collection: { type: "string", description: "Collection name" },
              documents: { type: "array", description: "Documents to insert" },
              auth_token: {
                type: "string",
                description: "Authorization token",
              },
            },
            required: ["collection", "documents", "auth_token"],
          },
        },
        {
          name: "mongo_update",
          description:
            "Update documents in MongoDB collection with authorization",
          inputSchema: {
            type: "object",
            properties: {
              collection: { type: "string", description: "Collection name" },
              filter: { type: "object", description: "MongoDB filter query" },
              update: { type: "object", description: "Update operations" },
              options: { type: "object", description: "Update options" },
              auth_token: {
                type: "string",
                description: "Authorization token",
              },
            },
            required: ["collection", "filter", "update", "auth_token"],
          },
        },
        {
          name: "mongo_delete",
          description:
            "Delete documents from MongoDB collection with authorization",
          inputSchema: {
            type: "object",
            properties: {
              collection: { type: "string", description: "Collection name" },
              filter: { type: "object", description: "MongoDB filter query" },
              auth_token: {
                type: "string",
                description: "Authorization token",
              },
            },
            required: ["collection", "filter", "auth_token"],
          },
        },
        {
          name: "mongo_aggregate",
          description: "Run aggregation pipeline with authorization",
          inputSchema: {
            type: "object",
            properties: {
              collection: { type: "string", description: "Collection name" },
              pipeline: { type: "array", description: "Aggregation pipeline" },
              options: { type: "object", description: "Aggregation options" },
              auth_token: {
                type: "string",
                description: "Authorization token",
              },
            },
            required: ["collection", "pipeline", "auth_token"],
          },
        },
      ],
    }));

    this.server.setRequestHandler(CallToolRequestSchema, async (request) => {
      const { name, arguments: args } = request.params;

      try {
        // Authorize request
        const authResult = await this.authMiddleware.authorize(
          args.auth_token,
          {
            operation: name,
            collection: args.collection,
          }
        );

        if (!authResult.authorized) {
          throw new Error(`Unauthorized: ${authResult.reason}`);
        }

        // Validate input
        const validationResult = this.validationMiddleware.validate(name, args);
        if (!validationResult.valid) {
          throw new Error(
            `Validation failed: ${validationResult.errors.join(", ")}`
          );
        }

        // Execute operation
        let result;
        switch (name) {
          case "mongo_find":
            result = await this.mongoTools.find(
              args.collection,
              args.filter,
              args.options
            );
            break;
          case "mongo_insert":
            result = await this.mongoTools.insert(
              args.collection,
              args.documents
            );
            break;
          case "mongo_update":
            result = await this.mongoTools.update(
              args.collection,
              args.filter,
              args.update,
              args.options
            );
            break;
          case "mongo_delete":
            result = await this.mongoTools.delete(args.collection, args.filter);
            break;
          case "mongo_aggregate":
            result = await this.mongoTools.aggregate(
              args.collection,
              args.pipeline,
              args.options
            );
            break;
          default:
            throw new Error(`Unknown tool: ${name}`);
        }

        return {
          content: [
            {
              type: "text",
              text: JSON.stringify(result, null, 2),
            },
          ],
        };
      } catch (error) {
        return {
          content: [
            {
              type: "text",
              text: `Error: ${error.message}`,
            },
          ],
          isError: true,
        };
      }
    });
  }
}
```

### Authorization Middleware

**Secure access control for database operations:**

```typescript
// mcp-mongo-server/src/middleware/auth.middleware.ts
import jwt from "jsonwebtoken";
import { Auth0Client } from "@repo/external-services";
import Redis from "ioredis";

export interface AuthContext {
  operation: string;
  collection: string;
  userId?: string;
  roles?: string[];
}

export interface AuthResult {
  authorized: boolean;
  reason?: string;
  userId?: string;
  roles?: string[];
}

export class AuthMiddleware {
  private auth0Client: Auth0Client;
  private redis: Redis;
  private permissions: Map<string, string[]>;

  constructor() {
    this.auth0Client = new Auth0Client();
    this.redis = new Redis(process.env.REDIS_URL);

    // Define collection permissions
    this.permissions = new Map([
      ["users", ["admin", "user"]],
      ["orders", ["admin", "manager", "user"]],
      ["products", ["admin", "manager"]],
      ["analytics", ["admin"]],
      ["logs", ["admin"]],
    ]);
  }

  async authorize(token: string, context: AuthContext): Promise<AuthResult> {
    try {
      // Check cache first
      const cacheKey = `auth:${token}:${context.operation}:${context.collection}`;
      const cached = await this.redis.get(cacheKey);

      if (cached) {
        const result = JSON.parse(cached);
        if (result.authorized) {
          return result;
        }
      }

      // Verify JWT token with Auth0
      const userProfile = await this.auth0Client.getUserProfile(token);
      const userId = userProfile.sub;
      const userRoles = userProfile.user_metadata?.roles || ["user"];

      // Check collection permissions
      const requiredRoles = this.permissions.get(context.collection);
      if (!requiredRoles) {
        return {
          authorized: false,
          reason: `Unknown collection: ${context.collection}`,
        };
      }

      const hasPermission = userRoles.some((role) =>
        requiredRoles.includes(role)
      );
      if (!hasPermission) {
        return {
          authorized: false,
          reason: `Insufficient permissions for collection: ${context.collection}`,
        };
      }

      // Check operation-specific permissions
      const operationAllowed = this.checkOperationPermission(
        context.operation,
        userRoles,
        context.collection
      );
      if (!operationAllowed) {
        return {
          authorized: false,
          reason: `Operation ${context.operation} not allowed for your role`,
        };
      }

      const result: AuthResult = {
        authorized: true,
        userId,
        roles: userRoles,
      };

      // Cache successful authorization for 5 minutes
      await this.redis.setex(cacheKey, 300, JSON.stringify(result));

      return result;
    } catch (error) {
      return {
        authorized: false,
        reason: `Authentication failed: ${error.message}`,
      };
    }
  }

  private checkOperationPermission(
    operation: string,
    roles: string[],
    collection: string
  ): boolean {
    // Admin can do everything
    if (roles.includes("admin")) {
      return true;
    }

    // Define operation-specific rules
    const writeOperations = ["mongo_insert", "mongo_update", "mongo_delete"];
    const readOperations = ["mongo_find", "mongo_aggregate"];

    if (readOperations.includes(operation)) {
      // Most roles can read
      return true;
    }

    if (writeOperations.includes(operation)) {
      // Only admin and manager can write to sensitive collections
      const sensitiveCollections = ["users", "orders", "analytics"];
      if (sensitiveCollections.includes(collection)) {
        return roles.includes("admin") || roles.includes("manager");
      }

      // Regular users can write to some collections
      return roles.includes("user") || roles.includes("manager");
    }

    return false;
  }
}
```

### Validation Middleware

**Input sanitization and validation:**

```typescript
// mcp-mongo-server/src/middleware/validation.middleware.ts
import Joi from "joi";

export interface ValidationResult {
  valid: boolean;
  errors: string[];
}

export class ValidationMiddleware {
  private schemas: Map<string, Joi.ObjectSchema>;

  constructor() {
    this.schemas = new Map([
      [
        "mongo_find",
        Joi.object({
          collection: Joi.string().alphanum().min(1).max(50).required(),
          filter: Joi.object().required(),
          options: Joi.object({
            limit: Joi.number().min(1).max(1000),
            skip: Joi.number().min(0),
            sort: Joi.object(),
            projection: Joi.object(),
          }).optional(),
          auth_token: Joi.string().required(),
        }),
      ],

      [
        "mongo_insert",
        Joi.object({
          collection: Joi.string().alphanum().min(1).max(50).required(),
          documents: Joi.array().items(Joi.object()).min(1).max(100).required(),
          auth_token: Joi.string().required(),
        }),
      ],

      [
        "mongo_update",
        Joi.object({
          collection: Joi.string().alphanum().min(1).max(50).required(),
          filter: Joi.object().required(),
          update: Joi.object().required(),
          options: Joi.object({
            upsert: Joi.boolean(),
            multi: Joi.boolean(),
          }).optional(),
          auth_token: Joi.string().required(),
        }),
      ],

      [
        "mongo_delete",
        Joi.object({
          collection: Joi.string().alphanum().min(1).max(50).required(),
          filter: Joi.object().required(),
          auth_token: Joi.string().required(),
        }),
      ],

      [
        "mongo_aggregate",
        Joi.object({
          collection: Joi.string().alphanum().min(1).max(50).required(),
          pipeline: Joi.array().items(Joi.object()).min(1).max(20).required(),
          options: Joi.object({
            allowDiskUse: Joi.boolean(),
            maxTimeMS: Joi.number().min(1).max(30000),
          }).optional(),
          auth_token: Joi.string().required(),
        }),
      ],
    ]);
  }

  validate(operation: string, args: any): ValidationResult {
    const schema = this.schemas.get(operation);
    if (!schema) {
      return {
        valid: false,
        errors: [`Unknown operation: ${operation}`],
      };
    }

    const { error } = schema.validate(args, { abortEarly: false });
    if (error) {
      return {
        valid: false,
        errors: error.details.map((detail) => detail.message),
      };
    }

    // Additional security checks
    const securityErrors = this.performSecurityChecks(operation, args);
    if (securityErrors.length > 0) {
      return {
        valid: false,
        errors: securityErrors,
      };
    }

    return { valid: true, errors: [] };
  }

  private performSecurityChecks(operation: string, args: any): string[] {
    const errors: string[] = [];

    // Check for dangerous operations
    if (args.filter && typeof args.filter === "object") {
      if (this.containsDangerousOperators(args.filter)) {
        errors.push("Dangerous MongoDB operators detected in filter");
      }
    }

    if (args.update && typeof args.update === "object") {
      if (this.containsDangerousOperators(args.update)) {
        errors.push("Dangerous MongoDB operators detected in update");
      }
    }

    // Check for injection patterns
    const stringFields = [args.collection];
    for (const field of stringFields) {
      if (field && this.containsInjectionPattern(field)) {
        errors.push("Potential injection pattern detected");
      }
    }

    return errors;
  }

  private containsDangerousOperators(obj: any): boolean {
    const dangerousOps = ["$where", "$eval", "$regex"];
    const objStr = JSON.stringify(obj);
    return dangerousOps.some((op) => objStr.includes(op));
  }

  private containsInjectionPattern(str: string): boolean {
    const patterns = [/\$\{.*\}/, /function\s*\(/, /eval\s*\(/];
    return patterns.some((pattern) => pattern.test(str));
  }
}
```

### MongoDB Tools Implementation

**Type-safe database operations:**

```typescript
// mcp-mongo-server/src/tools/mongo.tools.ts
import { Db, Collection, MongoError } from "mongodb";

export class MongoTools {
  private db: Db;

  constructor(db: Db) {
    this.db = db;
  }

  async find(collectionName: string, filter: any, options: any = {}) {
    try {
      const collection = this.db.collection(collectionName);
      const cursor = collection.find(filter, options);

      if (options.limit) cursor.limit(options.limit);
      if (options.skip) cursor.skip(options.skip);
      if (options.sort) cursor.sort(options.sort);

      const results = await cursor.toArray();
      return {
        success: true,
        data: results,
        count: results.length,
      };
    } catch (error) {
      throw new Error(`Find operation failed: ${error.message}`);
    }
  }

  async insert(collectionName: string, documents: any[]) {
    try {
      const collection = this.db.collection(collectionName);

      // Add metadata to documents
      const timestamp = new Date();
      const documentsWithMetadata = documents.map((doc) => ({
        ...doc,
        createdAt: timestamp,
        updatedAt: timestamp,
      }));

      const result = await collection.insertMany(documentsWithMetadata);
      return {
        success: true,
        insertedCount: result.insertedCount,
        insertedIds: result.insertedIds,
      };
    } catch (error) {
      throw new Error(`Insert operation failed: ${error.message}`);
    }
  }

  async update(
    collectionName: string,
    filter: any,
    update: any,
    options: any = {}
  ) {
    try {
      const collection = this.db.collection(collectionName);

      // Add updateAt timestamp
      const updateWithTimestamp = {
        ...update,
        $set: {
          ...(update.$set || {}),
          updatedAt: new Date(),
        },
      };

      const result = options.multi
        ? await collection.updateMany(filter, updateWithTimestamp, options)
        : await collection.updateOne(filter, updateWithTimestamp, options);

      return {
        success: true,
        matchedCount: result.matchedCount,
        modifiedCount: result.modifiedCount,
        upsertedCount: result.upsertedCount || 0,
        upsertedId: result.upsertedId,
      };
    } catch (error) {
      throw new Error(`Update operation failed: ${error.message}`);
    }
  }

  async delete(collectionName: string, filter: any) {
    try {
      const collection = this.db.collection(collectionName);
      const result = await collection.deleteMany(filter);

      return {
        success: true,
        deletedCount: result.deletedCount,
      };
    } catch (error) {
      throw new Error(`Delete operation failed: ${error.message}`);
    }
  }

  async aggregate(collectionName: string, pipeline: any[], options: any = {}) {
    try {
      const collection = this.db.collection(collectionName);
      const results = await collection.aggregate(pipeline, options).toArray();

      return {
        success: true,
        data: results,
        count: results.length,
      };
    } catch (error) {
      throw new Error(`Aggregation operation failed: ${error.message}`);
    }
  }
}
```

### Environment Configuration

**MCP Server environment variables:**

```bash
# MCP MongoDB Server Configuration
MCP_MONGO_PORT=3001
MCP_MONGO_LOG_LEVEL=info

# MongoDB Connection
MONGODB_URI=mongodb://localhost:27017/myapp
MONGODB_DATABASE=myapp
MONGODB_CONNECTION_POOL_SIZE=10

# Redis for Caching and Authorization
REDIS_URL=redis://localhost:6379
REDIS_AUTH_TTL=300

# Auth0 Integration
AUTH0_DOMAIN=your-domain.auth0.com
AUTH0_CLIENT_ID=your_client_id
AUTH0_CLIENT_SECRET=your_client_secret
AUTH0_AUDIENCE=https://your-api.auth0.com

# Security
MCP_RATE_LIMIT_MAX=100
MCP_RATE_LIMIT_WINDOW=60000
```

### Package Configuration

**Package.json for MCP server:**

```json
{
  "name": "@repo/mcp-mongo-server",
  "version": "1.0.0",
  "type": "module",
  "main": "dist/server.js",
  "scripts": {
    "build": "tsc",
    "start": "node dist/server.js",
    "dev": "tsx watch src/server.ts",
    "test": "jest",
    "test:integration": "jest --testPathPattern=integration"
  },
  "dependencies": {
    "@modelcontextprotocol/sdk": "^0.4.0",
    "mongodb": "^6.3.0",
    "ioredis": "^5.3.2",
    "joi": "^17.11.0",
    "jsonwebtoken": "^9.0.2",
    "@repo/external-services": "workspace:*",
    "@repo/shared": "workspace:*"
  },
  "devDependencies": {
    "@types/node": "^20.0.0",
    "@types/jsonwebtoken": "^9.0.5",
    "typescript": "^5.3.0",
    "tsx": "^4.6.0",
    "jest": "^29.7.0",
    "@types/jest": "^29.5.8"
  }
}
```

### Docker Integration

**Update docker-compose.yml to include MCP server:**

```yaml
# docker-compose.yml
version: "3.8"

services:
  mongodb:
    image: mongo:7
    ports:
      - "27017:27017"
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: password
    volumes:
      - mongodb_data:/data/db

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data

  mcp-mongo-server:
    build:
      context: .
      dockerfile: packages/mcp-mongo-server/Dockerfile
    ports:
      - "3001:3001"
    environment:
      - MONGODB_URI=mongodb://admin:password@mongodb:27017/myapp?authSource=admin
      - REDIS_URL=redis://redis:6379
      - AUTH0_DOMAIN=${AUTH0_DOMAIN}
      - AUTH0_CLIENT_ID=${AUTH0_CLIENT_ID}
      - AUTH0_CLIENT_SECRET=${AUTH0_CLIENT_SECRET}
    depends_on:
      - mongodb
      - redis
    volumes:
      - ./packages/mcp-mongo-server:/app
    command: npm run dev

  backend:
    build:
      context: .
      dockerfile: packages/backend/Dockerfile
    ports:
      - "3000:3000"
    environment:
      - MONGODB_URI=mongodb://admin:password@mongodb:27017/myapp?authSource=admin
      - REDIS_URL=redis://redis:6379
      - MCP_MONGO_URL=http://mcp-mongo-server:3001
    depends_on:
      - mongodb
      - redis
      - mcp-mongo-server

  frontend:
    build:
      context: .
      dockerfile: packages/frontend/Dockerfile
    ports:
      - "5173:5173"
    environment:
      - VITE_API_URL=http://localhost:3000
      - VITE_MCP_URL=http://localhost:3001
    depends_on:
      - backend

volumes:
  mongodb_data:
  redis_data:
```

### Usage Examples

**Using the MCP MongoDB server in your application:**

```typescript
// backend/src/services/mcp-client.service.ts
import { Client } from "@modelcontextprotocol/sdk/client/index.js";
import { StdioClientTransport } from "@modelcontextprotocol/sdk/client/stdio.js";

export class MCPClientService {
  private client: Client;
  private authToken: string;

  constructor(authToken: string) {
    this.authToken = authToken;
    this.client = new Client(
      {
        name: "backend-mcp-client",
        version: "1.0.0",
      },
      {
        capabilities: {
          tools: {},
        },
      }
    );
  }

  async initialize() {
    const transport = new StdioClientTransport({
      command: "node",
      args: ["../mcp-mongo-server/dist/server.js"],
    });
    await this.client.connect(transport);
  }

  async findUsers(filter: any, options?: any) {
    const result = await this.client.callTool({
      name: "mongo_find",
      arguments: {
        collection: "users",
        filter,
        options,
        auth_token: this.authToken,
      },
    });

    return JSON.parse(result.content[0].text);
  }

  async createUser(userData: any) {
    const result = await this.client.callTool({
      name: "mongo_insert",
      arguments: {
        collection: "users",
        documents: [userData],
        auth_token: this.authToken,
      },
    });

    return JSON.parse(result.content[0].text);
  }

  async updateUser(userId: string, updates: any) {
    const result = await this.client.callTool({
      name: "mongo_update",
      arguments: {
        collection: "users",
        filter: { _id: userId },
        update: { $set: updates },
        auth_token: this.authToken,
      },
    });

    return JSON.parse(result.content[0].text);
  }

  async getUserAnalytics(pipeline: any[]) {
    const result = await this.client.callTool({
      name: "mongo_aggregate",
      arguments: {
        collection: "users",
        pipeline,
        auth_token: this.authToken,
      },
    });

    return JSON.parse(result.content[0].text);
  }
}
```

### Frontend Integration

**React hook for MCP operations:**

```typescript
// frontend/src/hooks/useMCPMongo.ts
import { useState, useCallback } from "react";
import { useAuth } from "./useAuth";

export function useMCPMongo() {
  const { accessToken } = useAuth();
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState<string | null>(null);

  const callMCPTool = useCallback(
    async (toolName: string, args: any) => {
      if (!accessToken) {
        throw new Error("Not authenticated");
      }

      setLoading(true);
      setError(null);

      try {
        const response = await fetch("/api/mcp/call", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Authorization: `Bearer ${accessToken}`,
          },
          body: JSON.stringify({
            tool: toolName,
            arguments: {
              ...args,
              auth_token: accessToken,
            },
          }),
        });

        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`);
        }

        const result = await response.json();
        return result;
      } catch (err) {
        const errorMessage =
          err instanceof Error ? err.message : "Unknown error";
        setError(errorMessage);
        throw err;
      } finally {
        setLoading(false);
      }
    },
    [accessToken]
  );

  const findDocuments = useCallback(
    (collection: string, filter: any, options?: any) =>
      callMCPTool("mongo_find", { collection, filter, options }),
    [callMCPTool]
  );

  const insertDocuments = useCallback(
    (collection: string, documents: any[]) =>
      callMCPTool("mongo_insert", { collection, documents }),
    [callMCPTool]
  );

  const updateDocuments = useCallback(
    (collection: string, filter: any, update: any, options?: any) =>
      callMCPTool("mongo_update", { collection, filter, update, options }),
    [callMCPTool]
  );

  const deleteDocuments = useCallback(
    (collection: string, filter: any) =>
      callMCPTool("mongo_delete", { collection, filter }),
    [callMCPTool]
  );

  const aggregateDocuments = useCallback(
    (collection: string, pipeline: any[], options?: any) =>
      callMCPTool("mongo_aggregate", { collection, pipeline, options }),
    [callMCPTool]
  );

  return {
    loading,
    error,
    findDocuments,
    insertDocuments,
    updateDocuments,
    deleteDocuments,
    aggregateDocuments,
  };
}
```

### Testing Strategy

**Comprehensive testing for MCP server:**

```typescript
// mcp-mongo-server/src/__tests__/server.integration.test.ts
import { MCPMongoServer } from "../server";
import { MongoMemoryServer } from "mongodb-memory-server";
import { MongoClient } from "mongodb";
import Redis from "ioredis";

describe("MCP MongoDB Server Integration", () => {
  let mongoServer: MongoMemoryServer;
  let mongoClient: MongoClient;
  let redisClient: Redis;
  let mcpServer: MCPMongoServer;

  beforeAll(async () => {
    // Start in-memory MongoDB
    mongoServer = await MongoMemoryServer.create();
    const mongoUri = mongoServer.getUri();

    // Connect to MongoDB
    mongoClient = new MongoClient(mongoUri);
    await mongoClient.connect();

    // Start Redis (you might want to use redis-memory-server)
    redisClient = new Redis();

    // Set environment variables
    process.env.MONGODB_URI = mongoUri;
    process.env.REDIS_URL = "redis://localhost:6379";
    process.env.AUTH0_DOMAIN = "test.auth0.com";

    // Initialize MCP server
    mcpServer = new MCPMongoServer();
    await mcpServer.initialize();
  });

  afterAll(async () => {
    await mongoClient.close();
    await mongoServer.stop();
    await redisClient.quit();
  });

  beforeEach(async () => {
    // Clear collections before each test
    const db = mongoClient.db();
    const collections = await db.listCollections().toArray();
    for (const collection of collections) {
      await db.collection(collection.name).deleteMany({});
    }
  });

  describe("Authorization", () => {
    it("should reject requests with invalid tokens", async () => {
      // Test with invalid token
      const result = await mcpServer.callTool({
        name: "mongo_find",
        arguments: {
          collection: "users",
          filter: {},
          auth_token: "invalid-token",
        },
      });

      expect(result.isError).toBe(true);
      expect(result.content[0].text).toContain("Authentication failed");
    });

    it("should allow authorized operations", async () => {
      // Mock valid Auth0 token
      const mockToken = "valid-auth0-token";

      // Test successful operation (you'll need to mock Auth0 client)
      const result = await mcpServer.callTool({
        name: "mongo_find",
        arguments: {
          collection: "users",
          filter: {},
          auth_token: mockToken,
        },
      });

      expect(result.isError).toBe(false);
      const data = JSON.parse(result.content[0].text);
      expect(data.success).toBe(true);
    });
  });

  describe("MongoDB Operations", () => {
    const mockAuthToken = "valid-token";

    it("should insert and find documents", async () => {
      // Insert document
      const insertResult = await mcpServer.callTool({
        name: "mongo_insert",
        arguments: {
          collection: "users",
          documents: [{ name: "John Doe", email: "john@example.com" }],
          auth_token: mockAuthToken,
        },
      });

      expect(insertResult.isError).toBe(false);

      // Find document
      const findResult = await mcpServer.callTool({
        name: "mongo_find",
        arguments: {
          collection: "users",
          filter: { name: "John Doe" },
          auth_token: mockAuthToken,
        },
      });

      expect(findResult.isError).toBe(false);
      const data = JSON.parse(findResult.content[0].text);
      expect(data.data).toHaveLength(1);
      expect(data.data[0].name).toBe("John Doe");
    });

    it("should validate input parameters", async () => {
      // Test with invalid collection name
      const result = await mcpServer.callTool({
        name: "mongo_find",
        arguments: {
          collection: "invalid-collection-name-with-special-chars!",
          filter: {},
          auth_token: mockAuthToken,
        },
      });

      expect(result.isError).toBe(true);
      expect(result.content[0].text).toContain("Validation failed");
    });

    it("should prevent dangerous operations", async () => {
      // Test with dangerous $where operator
      const result = await mcpServer.callTool({
        name: "mongo_find",
        arguments: {
          collection: "users",
          filter: { $where: "this.name === 'admin'" },
          auth_token: mockAuthToken,
        },
      });

      expect(result.isError).toBe(true);
      expect(result.content[0].text).toContain("Dangerous MongoDB operators");
    });
  });
});
```

### Development Commands

```bash
# Install MCP server dependencies
yarn workspace @repo/mcp-mongo-server install

# Build MCP server
yarn workspace @repo/mcp-mongo-server build

# Start MCP server in development
yarn workspace @repo/mcp-mongo-server dev

# Run MCP server tests
yarn workspace @repo/mcp-mongo-server test
yarn workspace @repo/mcp-mongo-server test:integration

# Start entire stack with MCP server
docker-compose up -d

# Monitor MCP server logs
docker-compose logs -f mcp-mongo-server

# Test MCP server connectivity
curl -X POST http://localhost:3001/health
```

## 🔐 Authentication & Authorization

### Enterprise-Grade Authentication with Auth0

**🎯 Why Auth0 for Production Applications:**

✅ **Passwordless Authentication**: Email codes, SMS verification, and magic links  
✅ **30+ Social Providers**: Google, Facebook, GitHub, LinkedIn, Twitter, and more  
✅ **Enterprise SSO**: SAML, OIDC, Active Directory integration  
✅ **Advanced Security**: Multi-factor auth, anomaly detection, breached password detection  
✅ **Compliance Ready**: SOC2, GDPR, HIPAA compliance features  
✅ **Global CDN**: Ultra-fast authentication worldwide  
✅ **Free Tier**: 7,000 monthly active users

### Auth0 Implementation

**Complete passwordless and social authentication setup:**

```typescript
// external-services/src/clients/auth0.client.ts
import { AuthenticationApi, ManagementApi } from "auth0";

export class Auth0Client {
  private auth: AuthenticationApi;
  private mgmt: ManagementApi;

  constructor() {
    this.auth = new AuthenticationApi({
      domain: process.env.AUTH0_DOMAIN!,
      clientId: process.env.AUTH0_CLIENT_ID!,
      clientSecret: process.env.AUTH0_CLIENT_SECRET!,
    });
  }

  // Passwordless email login
  async sendPasswordlessEmail(email: string) {
    return this.auth.passwordless.sendEmail({
      email,
      send: "code",
      connection: "email",
    });
  }

  // Verify passwordless code
  async verifyPasswordlessCode(email: string, code: string) {
    return this.auth.passwordless.signIn({
      email,
      code,
      connection: "email",
    });
  }

  // Social login URLs
  getSocialLoginUrl(provider: "google" | "facebook" | "github") {
    return (
      `https://${process.env.AUTH0_DOMAIN}/authorize?` +
      `response_type=code&` +
      `client_id=${process.env.AUTH0_CLIENT_ID}&` +
      `connection=${provider}&` +
      `redirect_uri=${process.env.AUTH0_CALLBACK_URL}`
    );
  }
}
```

### Advanced Auth0 Features

**Enterprise-grade authentication capabilities:**

```typescript
// external-services/src/clients/auth0.client.ts (Extended)
import { AuthenticationApi, ManagementApi } from "auth0";

export class Auth0Client {
  private auth: AuthenticationApi;
  private mgmt: ManagementApi;

  constructor() {
    this.auth = new AuthenticationApi({
      domain: process.env.AUTH0_DOMAIN!,
      clientId: process.env.AUTH0_CLIENT_ID!,
      clientSecret: process.env.AUTH0_CLIENT_SECRET!,
    });

    this.mgmt = new ManagementApi({
      domain: process.env.AUTH0_DOMAIN!,
      clientId: process.env.AUTH0_CLIENT_ID!,
      clientSecret: process.env.AUTH0_CLIENT_SECRET!,
    });
  }

  // Passwordless SMS login
  async sendPasswordlessSMS(phoneNumber: string) {
    return this.auth.passwordless.sendSMS({
      phone_number: phoneNumber,
      connection: "sms",
    });
  }

  // Multi-factor authentication
  async sendMFAChallenge(mfaToken: string) {
    return this.auth.mfa.challenge({
      mfa_token: mfaToken,
      challenge_type: "otp",
    });
  }

  // Get user profile
  async getUserProfile(accessToken: string) {
    return this.auth.users.getInfo(accessToken);
  }

  // Update user metadata
  async updateUserMetadata(userId: string, metadata: any) {
    return this.mgmt.users.update({ id: userId }, { user_metadata: metadata });
  }
}
```

### Frontend Integration

**React hooks for Auth0 authentication:**

```typescript
// frontend/src/hooks/useAuth.ts
import { useState, useEffect } from "react";
import { Auth0Client } from "@repo/external-services";

export function useAuth() {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [accessToken, setAccessToken] = useState<string | null>(null);
  const authClient = new Auth0Client();

  useEffect(() => {
    // Check for existing token in localStorage
    const token = localStorage.getItem("auth0_access_token");
    if (token) {
      authClient
        .getUserProfile(token)
        .then((userProfile) => {
          setUser(userProfile);
          setAccessToken(token);
          setLoading(false);
        })
        .catch(() => {
          localStorage.removeItem("auth0_access_token");
          setLoading(false);
        });
    } else {
      setLoading(false);
    }
  }, []);

  const sendPasswordlessEmail = async (email: string) => {
    return authClient.sendPasswordlessEmail(email);
  };

  const verifyEmailCode = async (email: string, code: string) => {
    try {
      const result = await authClient.verifyPasswordlessCode(email, code);
      localStorage.setItem("auth0_access_token", result.access_token);
      const userProfile = await authClient.getUserProfile(result.access_token);
      setUser(userProfile);
      setAccessToken(result.access_token);
      return result;
    } catch (error) {
      throw error;
    }
  };

  const sendPasswordlessSMS = async (phoneNumber: string) => {
    return authClient.sendPasswordlessSMS(phoneNumber);
  };

  const getSocialLoginUrl = (provider: "google" | "facebook" | "github") => {
    return authClient.getSocialLoginUrl(provider);
  };

  const signOut = async () => {
    localStorage.removeItem("auth0_access_token");
    setUser(null);
    setAccessToken(null);
  };

  return {
    user,
    loading,
    accessToken,
    sendPasswordlessEmail,
    verifyEmailCode,
    sendPasswordlessSMS,
    getSocialLoginUrl,
    signOut,
  };
}
```

### Backend Integration

**Fastify plugin for Auth0 authentication:**

```typescript
// backend/src/plugins/auth.plugin.ts
import { FastifyPluginAsync } from "fastify";
import { Auth0Client } from "@repo/external-services";
import jwt from "jsonwebtoken";
import jwksClient from "jwks-rsa";

export const authPlugin: FastifyPluginAsync = async (fastify) => {
  const authClient = new Auth0Client();

  // JWKS client for token verification
  const client = jwksClient({
    jwksUri: `https://${process.env.AUTH0_DOMAIN}/.well-known/jwks.json`,
  });

  function getKey(header: any, callback: any) {
    client.getSigningKey(header.kid, (err, key) => {
      const signingKey = key?.getPublicKey();
      callback(null, signingKey);
    });
  }

  fastify.decorate("authenticate", async (request, reply) => {
    try {
      const token = request.headers.authorization?.replace("Bearer ", "");
      if (!token) {
        reply.code(401).send({ error: "No token provided" });
        return;
      }

      // Verify JWT token
      const decoded = await new Promise((resolve, reject) => {
        jwt.verify(
          token,
          getKey,
          {
            audience: process.env.AUTH0_CLIENT_ID,
            issuer: `https://${process.env.AUTH0_DOMAIN}/`,
            algorithms: ["RS256"],
          },
          (err, decoded) => {
            if (err) reject(err);
            else resolve(decoded);
          }
        );
      });

      // Get full user profile
      const userProfile = await authClient.getUserProfile(token);
      request.user = { ...decoded, profile: userProfile };
    } catch (error) {
      reply.code(401).send({ error: "Authentication failed" });
    }
  });

  // Optional: Role-based authorization
  fastify.decorate("authorize", (roles: string[]) => {
    return async (request: any, reply: any) => {
      if (!request.user) {
        reply.code(401).send({ error: "Not authenticated" });
        return;
      }

      const userRoles = request.user.profile?.user_metadata?.roles || [];
      const hasRole = roles.some((role) => userRoles.includes(role));

      if (!hasRole) {
        reply.code(403).send({ error: "Insufficient permissions" });
        return;
      }
    };
  });
};

// Usage in routes
fastify.get(
  "/protected",
  { preHandler: [fastify.authenticate] },
  async (request, reply) => {
    return { user: request.user };
  }
);

// Admin-only route
fastify.get(
  "/admin",
  { preHandler: [fastify.authenticate, fastify.authorize(["admin"])] },
  async (request, reply) => {
    return { message: "Admin access granted" };
  }
);
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
"Add Stripe payment processing with webhook handling"
"Create Resend email templates with React components"
"Add Twilio SMS verification with rate limiting"
"Build notification system with email and SMS providers"
"Implement passwordless login with Auth0 email codes"
"Add social login with Google, Facebook, and GitHub using Auth0"
"Create protected routes with JWT authentication middleware"
"Add multi-factor authentication with Auth0"
"Implement role-based authorization with Auth0 metadata"
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

# External Services
STRIPE_SECRET_KEY=sk_test_...
RESEND_API_KEY=re_...
TWILIO_ACCOUNT_SID=AC...
TWILIO_AUTH_TOKEN=...
TWILIO_PHONE_NUMBER=+1234567890

# Authentication
AUTH0_DOMAIN=your-domain.auth0.com
AUTH0_CLIENT_ID=your_client_id
AUTH0_CLIENT_SECRET=your_client_secret
AUTH0_CALLBACK_URL=http://localhost:3000/auth/callback
AUTH0_AUDIENCE=https://your-api.auth0.com

# App Configuration
APP_URL=http://localhost:3000
JWT_SECRET=your-jwt-secret-key
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
yarn workspace external-services add stripe
yarn workspace external-services add resend
yarn workspace external-services add twilio
yarn workspace external-services add @sendgrid/mail
yarn workspace external-services add auth0
yarn workspace external-services add jsonwebtoken @types/jsonwebtoken
yarn workspace external-services add jwks-rsa
yarn workspace mcp-mongo-server add @modelcontextprotocol/sdk
yarn workspace mcp-mongo-server add mongodb ioredis joi
yarn workspace shared build

# Redis commands
yarn workspace backend add ioredis @types/ioredis  # Redis client
yarn workspace backend add redis-commander         # Redis web UI

# MCP MongoDB Server commands
yarn workspace mcp-mongo-server add @modelcontextprotocol/sdk mongodb
yarn workspace mcp-mongo-server add ioredis joi jsonwebtoken
yarn workspace mcp-mongo-server add @types/jsonwebtoken @types/node
yarn workspace mcp-mongo-server test              # Run MCP server tests
yarn workspace mcp-mongo-server test:integration  # Integration tests
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

| Package               | Framework                                          | Purpose                                                     |
| --------------------- | -------------------------------------------------- | ----------------------------------------------------------- |
| **Frontend**          | Vitest + React Testing Library                     | Component and integration testing                           |
| **Backend**           | Node.js native test runner / Jest + Testcontainers | API endpoint and service testing with real databases        |
| **External Services** | Jest + Service Mocks                               | Third-party integration testing with mocked responses       |
| **Shared**            | Jest/Vitest                                        | Utility and type testing                                    |
| **Storybook**         | Play functions                                     | Interactive component testing                               |
| **Integration**       | Testcontainers                                     | Database and Redis integration tests with Docker containers |
| **Cache**             | Testcontainers + Redis                             | Redis caching logic testing with isolated containers        |

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
yarn workspace external-services test
yarn workspace external-services test:integration
```

### External Services Testing

**Mock-based Testing** for reliable third-party service integration:

```typescript
// external-services/src/__tests__/stripe.provider.test.ts
import { StripeProvider } from "../providers/stripe.provider";
import { jest } from "@jest/globals";

jest.mock("stripe", () => ({
  Stripe: jest.fn().mockImplementation(() => ({
    charges: {
      create: jest.fn().mockResolvedValue({
        id: "ch_test_123",
        status: "succeeded",
      }),
    },
  })),
}));

describe("StripeProvider", () => {
  let stripeProvider: StripeProvider;

  beforeEach(() => {
    stripeProvider = new StripeProvider();
  });

  it("should process payment successfully", async () => {
    const result = await stripeProvider.createCharge({
      amount: 2000,
      currency: "usd",
      source: "tok_visa",
    });

    expect(result.status).toBe("succeeded");
    expect(result.id).toBe("ch_test_123");
  });

  it("should handle webhook validation", async () => {
    // Test webhook signature validation and processing
  });
});

// external-services/src/__tests__/resend.provider.test.ts
import { ResendProvider } from "../providers/resend.provider";
import { jest } from "@jest/globals";

jest.mock("resend", () => ({
  Resend: jest.fn().mockImplementation(() => ({
    emails: {
      send: jest.fn().mockResolvedValue({
        id: "email_123",
        to: ["user@example.com"],
        from: "noreply@app.com",
        subject: "Welcome",
      }),
    },
  })),
}));

describe("ResendProvider", () => {
  let resendProvider: ResendProvider;

  beforeEach(() => {
    resendProvider = new ResendProvider();
  });

  it("should send email successfully", async () => {
    const result = await resendProvider.sendEmail({
      to: ["user@example.com"],
      from: "noreply@app.com",
      subject: "Welcome to our app",
      html: "<h1>Welcome!</h1>",
    });

    expect(result.id).toBe("email_123");
    expect(result.to).toContain("user@example.com");
  });
});

// external-services/src/__tests__/twilio.provider.test.ts
import { TwilioProvider } from "../providers/twilio.provider";
import { jest } from "@jest/globals";

jest.mock("twilio", () => ({
  Twilio: jest.fn().mockImplementation(() => ({
    messages: {
      create: jest.fn().mockResolvedValue({
        sid: "SM123456789",
        status: "queued",
        to: "+1234567890",
        from: "+0987654321",
      }),
    },
  })),
}));

describe("TwilioProvider", () => {
  let twilioProvider: TwilioProvider;

  beforeEach(() => {
    twilioProvider = new TwilioProvider();
  });

  it("should send SMS successfully", async () => {
    const result = await twilioProvider.sendSMS({
      to: "+1234567890",
      from: "+0987654321",
      body: "Your verification code is 123456",
    });

    expect(result.sid).toBe("SM123456789");
    expect(result.status).toBe("queued");
    expect(result.to).toBe("+1234567890");
  });

  it("should handle SMS delivery status webhook", async () => {
    // Test Twilio webhook processing for delivery status
  });
});

// external-services/src/__tests__/auth0.provider.test.ts
import { Auth0Client } from "../clients/auth0.client";
import { jest } from "@jest/globals";

jest.mock("auth0", () => ({
  AuthenticationApi: jest.fn().mockImplementation(() => ({
    passwordless: {
      sendEmail: jest.fn().mockResolvedValue({
        email: "user@example.com",
        status: "sent",
      }),
      signIn: jest.fn().mockResolvedValue({
        access_token: "test_token_123",
        token_type: "Bearer",
        expires_in: 86400,
      }),
    },
  })),
}));

describe("Auth0Client", () => {
  let auth0Client: Auth0Client;

  beforeEach(() => {
    auth0Client = new Auth0Client();
  });

  it("should send passwordless email successfully", async () => {
    const result = await auth0Client.sendPasswordlessEmail("user@example.com");

    expect(result.email).toBe("user@example.com");
    expect(result.status).toBe("sent");
  });

  it("should verify passwordless code successfully", async () => {
    const result = await auth0Client.verifyPasswordlessCode(
      "user@example.com",
      "123456"
    );

    expect(result.access_token).toBe("test_token_123");
    expect(result.token_type).toBe("Bearer");
  });

  it("should generate social login URLs correctly", async () => {
    const googleUrl = auth0Client.getSocialLoginUrl("google");

    expect(googleUrl).toContain("connection=google");
    expect(googleUrl).toContain("client_id=");
  });
});

// external-services/src/__tests__/auth0-extended.test.ts
import { Auth0Client } from "../clients/auth0.client";
import { jest } from "@jest/globals";

// Extended Auth0 testing with SMS and MFA
jest.mock("auth0", () => ({
  AuthenticationApi: jest.fn().mockImplementation(() => ({
    passwordless: {
      sendEmail: jest.fn().mockResolvedValue({
        email: "user@example.com",
        status: "sent",
      }),
      sendSMS: jest.fn().mockResolvedValue({
        phone_number: "+1234567890",
        status: "sent",
      }),
      signIn: jest.fn().mockResolvedValue({
        access_token: "test_token_123",
        token_type: "Bearer",
        expires_in: 86400,
      }),
    },
    mfa: {
      challenge: jest.fn().mockResolvedValue({
        challenge_type: "otp",
        oob_code: "test_oob_code",
      }),
    },
    users: {
      getInfo: jest.fn().mockResolvedValue({
        sub: "auth0|123456789",
        email: "user@example.com",
        name: "John Doe",
      }),
    },
  })),
  ManagementApi: jest.fn().mockImplementation(() => ({
    users: {
      update: jest.fn().mockResolvedValue({
        user_metadata: { role: "admin" },
      }),
    },
  })),
}));

describe("Auth0Client Extended Features", () => {
  let auth0Client: Auth0Client;

  beforeEach(() => {
    auth0Client = new Auth0Client();
  });

  it("should send passwordless SMS successfully", async () => {
    const result = await auth0Client.sendPasswordlessSMS("+1234567890");

    expect(result.phone_number).toBe("+1234567890");
    expect(result.status).toBe("sent");
  });

  it("should handle MFA challenge", async () => {
    const result = await auth0Client.sendMFAChallenge("test_mfa_token");

    expect(result.challenge_type).toBe("otp");
    expect(result.oob_code).toBe("test_oob_code");
  });

  it("should get user profile", async () => {
    const result = await auth0Client.getUserProfile("test_access_token");

    expect(result.sub).toBe("auth0|123456789");
    expect(result.email).toBe("user@example.com");
    expect(result.name).toBe("John Doe");
  });

  it("should update user metadata", async () => {
    const result = await auth0Client.updateUserMetadata("auth0|123456789", {
      role: "admin",
    });

    expect(result.user_metadata.role).toBe("admin");
  });
});
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

### External Services Enhancements

- **providers/**: Service abstraction layer (Stripe payments, Resend emails, Twilio SMS, Auth providers)
- **clients/**: HTTP clients for external APIs with retry logic and rate limiting
- **webhooks/**: Webhook handlers for payment confirmations, email events, SMS delivery status
- **adapters/**: Data transformation between external and internal formats
- **schemas/**: External API response/request validation schemas (Zod/Joi)
- **mocks/**: Mock implementations for testing and development environments
- **configs/**: Service-specific configuration and environment variables
- **templates/**: Email templates (React components for Resend) and SMS templates
- **auth/**: Authentication providers (Auth0, Supabase), JWT handling, social login strategies

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
yarn workspace external-services add stripe
yarn workspace external-services add resend
yarn workspace external-services add twilio
yarn workspace external-services add @sendgrid/mail
yarn workspace external-services add auth0
yarn workspace external-services add jsonwebtoken @types/jsonwebtoken
yarn workspace external-services add jwks-rsa
yarn workspace mcp-mongo-server add @modelcontextprotocol/sdk
yarn workspace mcp-mongo-server add mongodb ioredis joi

# Run tests
yarn test
yarn workspace backend test
yarn workspace backend test:integration  # Run with Testcontainers
yarn workspace frontend test
yarn workspace external-services test
yarn workspace external-services test:integration  # Test with service mocks
yarn workspace mcp-mongo-server test
yarn workspace mcp-mongo-server test:integration  # Test MCP server with containers

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

# MCP MongoDB Server development
yarn workspace mcp-mongo-server dev        # Start MCP server in watch mode
yarn workspace mcp-mongo-server build      # Build MCP server
docker-compose logs -f mcp-mongo-server    # Monitor MCP server logs
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

---

**Built with ❤️ using modern web technologies**
