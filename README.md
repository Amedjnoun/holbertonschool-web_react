# Holbertonschool Web React - TypeScript

This repository contains TypeScript projects focusing on fundamental TypeScript concepts and DOM manipulation.

## Project Description

**TypeScript - Amateur Level**  
*By: Johann Kerbrat, Engineering Manager at Uber Works*  
*Weight: 1*

### Learning Objectives

At the end of this project, you should be able to explain:

- Basic types in TypeScript
- Interfaces, Classes, and functions
- How to work with the DOM and TypeScript
- Generic types
- How to use namespaces
- How to merge declarations
- How to use an ambient Namespace to import an external library
- Basic nominal typing with TypeScript

### Requirements

- Allowed editors: vi, vim, emacs, Visual Studio Code
- All files should end with a new line
- All files will be transpiled on Ubuntu 18.04
- TS scripts will be checked with jest (version 24.9.*)
- Your code should use the `.ts` extension when possible
- The TypeScript compiler should not show any warning or error when compiling your code

### Configuration Files

The following configuration files should be copied to the appropriate task directories as specified in each task:

#### package.json
```json
{
  "name": "typescript_dependencies",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "mode": "development",
  "scripts": {
    "start-dev": "webpack-dev-server",
    "build": "webpack",
    "test": "jest"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@babel/plugin-proposal-export-default-from": "^7.18.10",
    "@babel/preset-typescript": "^7.22.15",
    "@types/jest": "^29.5.5",
    "eslint": "^9.24.0",
    "@typescript-eslint/eslint-plugin": "^8.29.1",
    "@typescript-eslint/parser": "^8.29.1",
    "clean-webpack-plugin": "^4.0.0",
    "fork-ts-checker-webpack-plugin": "^9.0.0",
    "html-webpack-plugin": "^5.5.3",
    "jest": "^29.7.0",
    "source-map": "^0.7.4",
    "ts-jest": "^29.1.1",
    "ts-loader": "^9.4.4",
    "typescript": "^4.9.5",
    "webpack": "^5.88.2",
    "webpack-cli": "^5.1.4",
    "webpack-dev-server": "^4.15.1"
  }
}
```

#### .eslintrc.js
```javascript
module.exports = {
  parser: '@typescript-eslint/parser',
  extends: [
    'plugin:@typescript-eslint/recommended',
  ],
  parserOptions: {
    ecmaVersion: 2020,
    sourceType: 'module',
    project: './tsconfig.json'
  },
  rules: {
  },
}
```

#### tsconfig.json
```json
{
  "compilerOptions": {
    "outDir": "./dist/",
    "sourceMap": true,
    "noImplicitAny": true,
    "module": "es6",
    "target": "es5",
    "allowJs": true,
    "moduleResolution": "node",
    "skipLibCheck": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "lib": ["ES2020", "DOM"],
    "strict": true
  }
}
```

#### webpack.config.js
```javascript
const path = require("path");
const HtmlWebpackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');
const ForkTsCheckerWebpackPlugin = require('fork-ts-checker-webpack-plugin');

module.exports = {
  mode: "development",
  entry: "./js/main.ts",
  
  devtool: "inline-source-map",
  
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        loader: 'ts-loader',
        options: {
          transpileOnly: true
        }
      }
    ]
  },
  
  resolve: {
    extensions: [".tsx", ".ts", ".js"]
  },
  
  devServer: {
    static: {
      directory: path.join(__dirname, 'dist'),
    },
    open: true,
    port: 8080,
  },
  
  plugins: [
    new ForkTsCheckerWebpackPlugin(),
    new CleanWebpackPlugin(),
    new HtmlWebpackPlugin({
      title: "Development"
    })
  ],
  
  output: {
    filename: "bundle.js",
    path: path.resolve(__dirname, "dist")
  }
};
```

### Tasks Overview

- **Task 0**: Creating an interface for a student
- **Task 1**: Building a Teacher interface with optional properties
- **Task 2**: Extending interfaces and creating Director interface
- **Task 3**: Function interfaces and StudentClass implementation
- **Task 4**: Writing a complete class with interfaces
- **Task 5**: Advanced types and employee management
- **Task 6**: Creating functions specific to employees
- **Task 7**: String literal types
- **Task 8**: Ambient Namespaces and external libraries
- **Task 9**: Namespace & Declaration merging
- **Task 10**: Brand convention & Nominal typing

### Directory Structure

```
TypeScript/
├── task_0/
│   ├── js/
│   │   └── main.ts
│   ├── package.json
│   ├── .eslintrc.js
│   ├── tsconfig.json
│   └── webpack.config.js
├── task_1/
│   ├── js/
│   │   └── main.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── webpack.config.js
├── task_2/
│   ├── js/
│   │   └── main.ts
│   ├── package.json
│   ├── tsconfig.json
│   └── webpack.config.js
├── task_3/
│   ├── js/
│   │   ├── main.ts
│   │   ├── interface.ts
│   │   ├── crud.d.ts
│   │   └── crud.js
│   ├── package.json
│   ├── tsconfig.json
│   └── webpack.config.js
├── task_4/
│   ├── js/
│   │   └── subjects/
│   │       ├── Teacher.ts
│   │       ├── Subject.ts
│   │       ├── Cpp.ts
│   │       ├── React.ts
│   │       └── Java.ts
│   ├── package.json
│   └── tsconfig.json
└── task_5/
    ├── js/
    │   └── main.ts
    ├── package.json
    ├── tsconfig.json
    └── webpack.config.js
```

### Task Details

#### Task 0: Student Interface & DOM Manipulation
- Create a Student interface with firstName, lastName, age, and location properties
- Render a table with student data using vanilla JavaScript and TypeScript

#### Task 1-4: Teacher Interfaces & Classes
- Build Teacher interface with readonly properties and index signatures
- Extend Teacher interface to create Directors interface
- Implement function interfaces and StudentClass with proper TypeScript typing

#### Task 5-7: Advanced Types
- Create Director and Teacher classes with specific interfaces
- Implement employee creation functions with union types
- Use type predicates and string literal types

#### Task 8: Ambient Namespaces
- Work with external JavaScript libraries using ambient declarations
- Create type definitions for CRUD operations
- Use triple-slash directives for dependencies

#### Task 9: Namespaces & Declaration Merging
- Implement namespace organization for subject classes
- Use declaration merging to extend interfaces
- Create modular TypeScript architecture

#### Task 10: Nominal Typing
- Implement brand convention for type safety
- Create distinct types for MajorCredits and MinorCredits
- Use branded types to prevent accidental type mixing

### Setup Instructions

1. Navigate to each task directory
2. Run `npm install` to install dependencies
3. Run `npm run build` to compile TypeScript
4. Check that compilation completes without errors

### Testing

Each task can be tested by running:
```bash
npm run build
```

The TypeScript compiler should return "No type errors found" for successful completion.

### Resources

- [TypeScript in 5 minutes](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [TypeScript DOM Manipulation](https://www.typescriptlang.org/docs/handbook/dom-manipulation.html)
- [TypeScript Object Types](https://www.typescriptlang.org/docs/handbook/2/objects.html)
- [TSConfig Reference](https://www.typescriptlang.org/tsconfig)
