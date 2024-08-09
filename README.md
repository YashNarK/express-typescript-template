# Table of Contents

- [Table of Contents](#table-of-contents)
- [Template for Express + TypeScript Project](#template-for-express--typescript-project)
  - [1. create a folder called `express-typescript-template` and cd into it.](#1-create-a-folder-called-express-typescript-template-and-cd-into-it)
  - [2. Add a .gitignore file](#2-add-a-gitignore-file)
  - [3. Initialize an npm project](#3-initialize-an-npm-project)
  - [4. Install dependencies](#4-install-dependencies)
  - [5. Create SRC folder and entry point](#5-create-src-folder-and-entry-point)
  - [6. Initialize TypeScript Configuration](#6-initialize-typescript-configuration)
  - [7. Initialize ESLint Configuration](#7-initialize-eslint-configuration)
    - [Override es-lint version](#override-es-lint-version)
  - [8. Setup the folder structure](#8-setup-the-folder-structure)
    - [Recommended Folder Structure](#recommended-folder-structure)
    - [Command to create folder structures](#command-to-create-folder-structures)
  - [9. Setup .env file](#9-setup-env-file)
  - [10. Write index.ts code](#10-write-indexts-code)
  - [11. Write server.ts code:](#11-write-serverts-code)
  - [12. Update package.json with scripts to run for dev; build and start for production. And type as module.](#12-update-packagejson-with-scripts-to-run-for-dev-build-and-start-for-production-and-type-as-module)
    - [Explanation of Scripts:](#explanation-of-scripts)
    - [Additional Notes:](#additional-notes)
    - [Summary of commands](#summary-of-commands)
  - [13. Using Config library to maintain different configurations](#13-using-config-library-to-maintain-different-configurations)
    - [**Step 1: Install the Necessary Packages**](#step-1-install-the-necessary-packages)
    - [**Step 2: Create the `config` Directory**](#step-2-create-the-config-directory)
    - [**Step 3: Define Environment-Specific Configuration Files**](#step-3-define-environment-specific-configuration-files)
    - [**Step 4: Populate the Configuration Files**](#step-4-populate-the-configuration-files)
    - [**Step 5: Access Configuration in Your Application**](#step-5-access-configuration-in-your-application)
    - [**Step 6: Environment Variable Overrides**](#step-6-environment-variable-overrides)
    - [**Step 7: Use `dotenv` for Environment Variables**](#step-7-use-dotenv-for-environment-variables)
    - [**Step 8: Document and Secure Your Configurations**](#step-8-document-and-secure-your-configurations)
    - [**Step 9: Set Up Configuration for Different Environments in Deployment**](#step-9-set-up-configuration-for-different-environments-in-deployment)
    - [**Conclusion**](#conclusion)
- [Best Express JS development practices:](#best-express-js-development-practices)
  - [1. **Project Structure**](#1-project-structure)
  - [2. **TypeScript Integration**](#2-typescript-integration)
  - [3. **Middleware Management**](#3-middleware-management)
  - [4. **Security Best Practices**](#4-security-best-practices)
  - [5. **Performance Optimization**](#5-performance-optimization)
  - [6. **Testing**](#6-testing)
  - [7. **Error Handling**](#7-error-handling)
  - [8. **Logging**](#8-logging)
  - [9. **API Design**](#9-api-design)
  - [10. **Documentation**](#10-documentation)
  - [11. **Deployment \& Monitoring**](#11-deployment--monitoring)
  - [12. **Environment Management**](#12-environment-management)
  - [13. **Advanced Error Handling and Logging**](#13-advanced-error-handling-and-logging)

# Template for Express + TypeScript Project

## 1. create a folder called `express-typescript-template` and cd into it.

```bash
mkdir express-typescript-template && cd express-typescript-template
```

## 2. Add a .gitignore file

Add a .gitignore file with the contents copied from https://github.com/github/gitignore/blob/main/Node.gitignore

## 3. Initialize an npm project

```bash
npm init -y
```

## 4. Install dependencies

```bash
npm i express dotenv helmet morgan
npm i -D typescript ts-node tsx @types/node @types/express @types/morgan @types/helmet nodemon eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin jest prettier tsconfig-paths

# -----------------------------------------------------------------------------------------------------------------------------------------------------------
# INITIAL TEMPLATE DEPENDENCIES
# -----------------------------------------------------------------------------------------------------------------------------------------------------------


### Essential Dependencies:
# - **`express`**: The core framework for building your API.
# - **`dotenv`**: For managing environment variables.
# - **`helmet`**: Adds security-related HTTP headers to your Express app.
# - **`morgan`**: A logging middleware for requests.

### TypeScript and Dev Dependencies:
# - **`typescript`**: The TypeScript compiler.
# - **`ts-node`**: Allows TypeScript to be run directly in Node.js.
# - **`tsx`**: ts-node but better.
# - **`@types/node`**: Type definitions for Node.js.
# - **`@types/express`**: Type definitions for Express.

### Additional Recommendations:
# - **`nodemon`**: For automatic restarting of the server during development.
# - **`eslint`**: For linting your TypeScript code.
# - **`@typescript-eslint/parser`** and **`@typescript-eslint/eslint-plugin`**: For integrating ESLint with TypeScript.
# - **`jest`** or **`mocha`**, **`chai`**, **`supertest`**: For testing your application.
# - **`prettier`**: For code formatting.
# - **`cross-env`**: To set environment variables across different OS.
# - **`tsconfig-paths`**: To use custom path mappings in TypeScript.

# -----------------------------------------------------------------------------------------------------------------------------------------------------------
# PRODUCTION GRADE DEPENDENCIES
# -----------------------------------------------------------------------------------------------------------------------------------------------------------

### 1. **Logging and Monitoring:**
#    - **`winston`** or **`pino`**: A more sophisticated logging library than `morgan`, useful for production environments.
#    - **`express-winston`**: Middleware for logging HTTP requests and responses using `winston`.
#    - **`prom-client`**: For Prometheus metrics if you want to monitor your application's performance.

### 2. **Error Handling:**
#    - **`express-async-errors`**: Automatically handles errors thrown in async routes/middleware.
#    - **`http-errors`**: For creating HTTP errors easily.

### 3. **Database:**
#    - **`mongoose`**: If you’re using MongoDB.
#    - **`pg`**: If you’re using PostgreSQL.
#    - **`sequelize`**: For an ORM that supports multiple databases.
#    - **`typeorm`**: Another ORM option that supports TypeScript well.

### 4. **Authentication and Security:**
#    - **`passport`** and **`passport-jwt`**: For authentication strategies, especially JWT.
#    - **`express-rate-limit`**: To protect your API from brute-force attacks.
#    - **`csurf`**: For CSRF protection.
#    - **`bcryptjs`**: For hashing passwords.

### 5. **CORS:**
#    - **`cors`**: Middleware to enable Cross-Origin Resource Sharing, especially useful if your frontend and backend are on different domains.

### 6. **Compression:**
#    - **`compression`**: Middleware to gzip compress responses, reducing the size of the response body and improving performance.

### 7. **Caching:**
#    - **`redis`**: For caching and session management.
#    - **`express-session`**: For session management, especially with Redis.

### 8. **Validation:**
#    - **`class-validator`**: Decorator-based validation library for TypeScript and JavaScript, often used with `class-transformer`.
#    - **`class-transformer`**: Transforms plain objects into class objects and vice versa, useful for validation and data handling.
#    - **`joi`**: Another popular validation library that provides a powerful schema description language and data validator for JavaScript.


```

## 5. Create SRC folder and entry point

```bash
mkdir src && touch src/index.ts
```

## 6. Initialize TypeScript Configuration

```bash
npx tsc --init --module NodeNext --moduleResolution NodeNext --target ES2020 --rootDir ./src --outDir ./dist --esModuleInterop --strict

# Explanation of the Flags:

# - **`--module NodeNext`**: setting this in your TypeScript configuration is correct if you’re aiming to use the latest module resolution strategy that aligns with Node.js’s native ESM support.

# - **`--moduleResolution NodeNext`**: The nodenext module resolution strategy is used in TypeScript for modern versions of Node.js, specifically Node.js v12 and later. This strategy is designed to handle both ECMAScript imports and CommonJS require, which resolve using different algorithms. nodenext is the correct module resolution option if you are targeting Node 16+ (or really 12+ with some caveats about async/await and certain package.json exports features)

# - **`--target ES2020`**: Sets the output to be compatible with ES2020, allowing modern JavaScript features.
# - **`--rootDir ./src`**: Specifies the root directory of your source files.
# - **`--outDir ./dist`**: Specifies the output directory for the compiled JavaScript files.
# - **`--esModuleInterop`**: Ensures compatibility between CommonJS and ES Module imports/exports.
# - **`--strict`**: Enables all strict type-checking options.


```

This will generate a `tsconfig.json` with these options pre-configured. You can then further tweak the `tsconfig.json` file as needed. Other options not covered by the command-line flags can be added manually.

## 7. Initialize ESLint Configuration

```bash
npx eslint --init

# FOLLOWING ARE THE CHOICES I MADE FOR THE PROJECT
# You can also run this command directly using 'npm init @eslint/config@latest'.

# > express-typescript-template@1.0.0 npx
# > create-config

# @eslint/create-config: v1.2.0

# √ How would you like to use ESLint? · problems
# √ What type of modules does your project use? · esm
# √ Which framework does your project use? · none
# √ Does your project use TypeScript? · typescript
# √ Where does your code run? · node
# The config that you've selected requires the following dependencies:

# eslint@9.x, globals, @eslint/js, typescript-eslint
# √ Would you like to install them now? · No / Yes
# √ Which package manager do you want to use? · npm
```

### Override es-lint version

- I received the following warning message, I will be adding that line to package.json manually.

```plaintext
Successfully created D:\Projects\express-typescript-template\eslint.config.mjs file.
Note that some plugins currently do not support ESLint v9 yet.
You may need to use '--force' when installing, or add the following to your package.json:
"overrides": { "eslint": "^9.8.0" }
```

## 8. Setup the folder structure

### Recommended Folder Structure

```bash
# /src
# │   /config          # Configuration files (e.g., database, environment)
# │   /controllers     # Request handlers
# │   /interfaces      # TypeScript interfaces and types
# │   /middlewares     # Custom middleware
# │   /models          # Database models (e.g., Mongoose models)
# │   /routes          # Route definitions
# │   /services        # Business logic
# │   /utils           # Utility functions
# │   /validators      # Request validation logic
# │   index.ts         # Entry point of the application
# │   server.ts        # Server setup and configuration
# / .env               # Environment variables
# / .gitignore         # Git ignore file
# / package.json       # Node.js dependencies and scripts
# / tsconfig.json      # TypeScript configuration
# /eslint.config.mjs   # es-lint configuration
```

### Command to create folder structures

```bash
mkdir -p src/config src/controllers src/interfaces src/middlewares src/models src/routes src/services src/utils src/validators && touch src/server.ts .env

```

## 9. Setup .env file

- Add the port number to the .env file as a environment variable

```plaintext
PORT=3000

```

## 10. Write index.ts code

```ts
// src\index.ts

import express from "express";
import dotenv from "dotenv";
import morgan from "morgan";
import helmet from "helmet";

// Initialize dotenv to load environment variables from .env file
dotenv.config();

const app = express();

// Use Helmet for setting security-related HTTP headers
app.use(helmet());

// Use Morgan for logging HTTP requests
app.use(morgan("dev"));

// Middleware to parse JSON bodies
app.use(express.json());

// Define a simple route
app.get("/", (req, res) => {
  res.send("Hello, TypeScript with Express!");
});

export default app;
```

## 11. Write server.ts code:

```ts
// src\server.ts
import app from "./index.js";

const PORT = process.env.PORT || 3000;

// Start the server
app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
```

## 12. Update package.json with scripts to run for dev; build and start for production. And type as module.

```json
{
  // ...,
  "scripts": {
    "start": "node dist/server.js",
    "dev": "nodemon --exec \"npx tsx src/server.ts \"  ",
    "build": "tsc",
    "lint": "eslint . --ext .ts",
    "format": "prettier --write 'src/**/*.ts'"
  },
  "type": "module"
  // ...
}
```

### Explanation of Scripts:

- **`start`**: Builds the TypeScript code and runs the compiled JavaScript with Node.js. This script is intended for production use.

  ```bash
  node dist/server.js
  ```

- **`dev`**: Uses `nodemon` to automatically restart the server when changes are detected in your TypeScript files. This script is for development.

  ```bash
  nodemon --exec "npx tsx src/server.ts"
  ```

- **`build`**: Compiles TypeScript code into JavaScript and outputs it to the `dist` directory.

  ```bash
  tsc
  ```

- **`lint`**: Runs ESLint to check for linting issues in your TypeScript files.

  ```bash
  eslint . --ext .ts
  ```

- **`format`**: Formats your TypeScript files using Prettier.

  ```bash
  prettier --write 'src/**/*.ts'
  ```

- **`"type":"module"`**: Including this in your package.json is a way to tell Node.js that you are using ECMAScript modules (ESM) in your project. This means that .js files within the package will be treated as ESM, and you should use import and export statements instead of require() and module.exports which are used in CommonJS (CJS) modules.

### Additional Notes:

- Ensure that you have the `server.ts` file properly configured in your `src` directory.
- If you make changes to the TypeScript files, use the `build` script to compile them before running the `start` script.
- For development, simply use `npm run dev` to start the server with `nodemon` monitoring changes.

### Summary of commands

```bash
# DEVELOPMENT MODE SERVER START UP
npm run dev

# PRODUCTION MODE

# BUILD DISTRIBUTION FILES
npm run build

# START SERVER USING DIST
npm run start
```

## 13. Using Config library to maintain different configurations
Organizing environment-specific configurations is crucial for managing different environments like development, staging, and production in a scalable and maintainable way. Below is a step-by-step guide on how to achieve this using a `config` directory and a configuration management library, such as `config` or `dotenv-flow`.

### **Step 1: Install the Necessary Packages**
To manage environment-specific configurations effectively, you can use the `config` package. It allows you to define configuration files for different environments.

```bash
npm install config
```

### **Step 2: Create the `config` Directory**
In the root of your project, create a `config` directory. This will house your environment-specific configuration files.

```bash
mkdir config
```

### **Step 3: Define Environment-Specific Configuration Files**
In the `config` directory, create JSON or YAML files for each environment. For example:

- `default.json`: Common configurations for all environments.
- `development.json`: Configurations specific to the development environment.
- `production.json`: Configurations specific to the production environment.
- `test.json`: Configurations specific to the testing environment.

Here's an example structure:

```
config/
│
├── default.json
├── development.json
├── production.json
└── test.json
```

### **Step 4: Populate the Configuration Files**
Define your configurations in these files. Here’s an example for `default.json`:

```json
{
  "app": {
    "port": 3000,
    "name": "MyApp"
  },
  "db": {
    "host": "localhost",
    "port": 27017,
    "name": "myapp_db"
  }
}
```

In `development.json`, you might override some of these settings:

```json
{
  "app": {
    "port": 3001
  },
  "db": {
    "host": "localhost",
    "port": 27017,
    "name": "myapp_dev_db"
  }
}
```

And in `production.json`:

```json
{
  "app": {
    "port": 8080
  },
  "db": {
    "host": "prod-db-host",
    "port": 27017,
    "name": "myapp_prod_db"
  }
}
```

### **Step 5: Access Configuration in Your Application**
Now, you can access the configurations in your application using the `config` module:

```typescript
import config from 'config';

const port = config.get<number>('app.port');
const dbHost = config.get<string>('db.host');

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});
```

### **Step 6: Environment Variable Overrides**
You can also override configuration values using environment variables. The `config` library automatically looks for environment variables matching your configuration keys.

For example, if you want to override `db.host`, you can set an environment variable like this:

```bash
export db__host=production-db-host
```

The `config` library will recognize `db__host` as an override for the `db.host` setting.

### **Step 7: Use `dotenv` for Environment Variables**
You might also need to manage secrets or other environment-specific values that should not be committed to source control. For this, use `dotenv` in combination with `config`.

1. **Install `dotenv`**:
   ```bash
   npm install dotenv
   ```

2. **Create a `.env` file**:
   In the root of your project, create a `.env` file and add your environment-specific variables:

   ```env
   DB_PASSWORD=supersecretpassword
   JWT_SECRET=mysecretjwtkey
   ```

3. **Load `.env` Variables**:
   Add this to the entry point of your application (e.g., `index.ts` or `server.ts`):

   ```typescript
   import dotenv from 'dotenv';
   dotenv.config();
   ```

   Now, you can use these environment variables in your `config` files or directly in your application:

   ```typescript
   const dbPassword = process.env.DB_PASSWORD;
   const jwtSecret = process.env.JWT_SECRET;
   ```

### **Step 8: Document and Secure Your Configurations**
1. **`.env.example` File**: Create a `.env.example` file in the root directory that lists all the environment variables required by your application, along with example values. This will help new developers get up and running quickly.

   ```env
   DB_PASSWORD=your_db_password
   JWT_SECRET=your_jwt_secret
   ```

2. **Git Ignore Sensitive Files**: Ensure that your `.env` files are listed in `.gitignore` to prevent them from being committed to version control:

   ```
   # .gitignore
   .env
   ```

### **Step 9: Set Up Configuration for Different Environments in Deployment**
When deploying your application, ensure that the correct environment variables are set in your production environment, and that the correct configuration file is being used by setting the `NODE_ENV` environment variable:

```bash
export NODE_ENV=production
npm start
```

### **Conclusion**
By organizing environment-specific configurations in a separate `config` directory and using a configuration management library, you ensure that your application is flexible, maintainable, and secure across different environments. This approach also makes it easier to manage and scale as your application grows.

# Best Express JS development practices:

When developing advanced Express.js applications, focusing on best practices can significantly improve the maintainability, performance, and security of your application. Here’s a comprehensive guide to advanced Express.js development practices:

## 1. **Project Structure**

- **Modular Folder Structure:** Organize your application by feature or module rather than by function (e.g., controllers, services, routes). This makes the codebase more scalable and easier to navigate.
- **Layered Architecture:** Implement a clear separation of concerns by splitting your code into layers such as controller, service, repository, and model.
- **Use Domain-Driven Design (DDD):** For complex applications, DDD can help to encapsulate the business logic and manage the complexity.

## 2. **TypeScript Integration**

- **Strict Typing:** Use TypeScript’s strict mode to catch potential errors during development.
- **DTOs and Interfaces:** Define Data Transfer Objects (DTOs) and interfaces to ensure consistent data structures across your application.
- **Advanced Types:** Leverage advanced TypeScript features like generics, union types, and conditional types to create flexible and reusable components.

## 3. **Middleware Management**

- **Modular Middlewares:** Create modular and reusable middlewares for cross-cutting concerns like logging, authentication, and error handling.
- **Asynchronous Middlewares:** Ensure your middlewares are asynchronous where applicable to prevent blocking the event loop.
- **Error Handling Middleware:** Implement a centralized error handling middleware to manage errors consistently across the application.

## 4. **Security Best Practices**

- **Helmet:** Use the Helmet middleware to secure your app by setting various HTTP headers.
- **Rate Limiting:** Implement rate limiting to prevent brute force attacks and DDoS.
- **Input Validation and Sanitization:** Always validate and sanitize user input using libraries like `Joi` or `express-validator` to prevent injection attacks.
- **CORS Management:** Properly configure CORS to control which domains can access your API.

## 5. **Performance Optimization**

- **Caching:** Implement caching strategies using Redis or in-memory caches to reduce load times for frequent requests.
- **Lazy Loading:** Use lazy loading for routes or components that are not immediately needed to reduce initial load times.
- **Compression:** Use `compression` middleware to compress response bodies for better performance.
- **Cluster Mode:** Use the Node.js cluster module or PM2 to scale your application across multiple CPU cores.

## 6. **Testing**

- **Unit Testing:** Write unit tests for individual components like controllers, services, and utilities using Jest or Mocha.
- **Integration Testing:** Test the integration between different modules and services.
- **E2E Testing:** Implement end-to-end testing using tools like Cypress or Puppeteer to simulate real-world scenarios.
- **Test Coverage:** Ensure high test coverage and use coverage tools like Istanbul to identify untested parts of the codebase.

## 7. **Error Handling**

- **Centralized Error Handling:** Implement a centralized error handler to manage and log errors consistently.
- **Custom Error Classes:** Create custom error classes to represent different types of errors in your application.
- **Graceful Shutdown:** Implement graceful shutdown procedures to handle cleanup tasks and prevent data loss during unexpected shutdowns.

## 8. **Logging**

- **Structured Logging:** Use a structured logging library like `Winston` or `Pino` to capture logs in a structured format (e.g., JSON).
- **Log Levels:** Implement different log levels (e.g., info, debug, warn, error) to control the verbosity of logs in different environments.
- **Centralized Log Management:** Use a centralized log management system like ELK Stack or AWS CloudWatch for better log aggregation and monitoring.

## 9. **API Design**

- **RESTful API Principles:** Follow RESTful principles when designing your API endpoints, using proper HTTP methods, status codes, and URIs.
- **Pagination and Filtering:** Implement pagination, filtering, and sorting for endpoints that return large datasets.
- **Versioning:** Version your API endpoints to manage breaking changes without disrupting existing clients.
- **Rate Limiting:** Protect your APIs from abuse by implementing rate limiting.

## 10. **Documentation**

- **API Documentation:** Use tools like Swagger or Postman to create interactive API documentation.
- **In-Code Documentation:** Maintain proper in-code documentation with JSDoc or TypeDoc for better developer experience.
- **ReadMe and Contribution Guides:** Keep a well-documented README and contribution guide for onboarding new developers.

## 11. **Deployment & Monitoring**

- **CI/CD Pipelines:** Implement continuous integration and continuous deployment pipelines using tools like GitHub Actions, Jenkins, or CircleCI.
- **Containerization:** Use Docker to containerize your application for consistent deployments across different environments.
- **Monitoring & Alerting:** Integrate monitoring tools like Prometheus, Grafana, or New Relic to monitor application performance and set up alerts for critical issues.

## 12. **Environment Management**

- **Environment Variables:** Use environment variables to manage configuration settings securely. Tools like dotenv can help load these variables.
- **Secret Management:** Store sensitive data like API keys and passwords securely using services like AWS Secrets Manager or HashiCorp Vault.
- **Environment Segmentation:** Separate environments for development, staging, and production to ensure consistent behavior across the application lifecycle.

## 13. **Advanced Error Handling and Logging**

- **Correlation IDs:** Use correlation IDs to trace and debug issues across multiple microservices or distributed systems.
- **Advanced Logging with Context:** Log with context, such as request and user information, to make logs more meaningful.

By incorporating these advanced practices into your Express.js development workflow, you can build robust, scalable, and maintainable applications that are well-equipped to handle complex business requirements.
