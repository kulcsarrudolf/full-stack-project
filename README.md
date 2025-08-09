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

# Run tests
yarn test
yarn workspace backend test
yarn workspace backend test:integration  # Run with Testcontainers
yarn workspace frontend test
yarn workspace external-services test
yarn workspace external-services test:integration  # Test with service mocks

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
