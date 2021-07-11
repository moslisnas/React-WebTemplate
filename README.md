# React-WebTemplate
React web project templates.

This project can be used to generate your own applications.

Actually available:
* React v17.0.2 - latest version at 11/07/2021
* React v17.0.2 with Next.js - latest version at 11/07/2021

## React latest version
### React latest version install:
* First we install node from this link: https://nodejs.org/dist/v14.17.3/node-v14.17.3-x64.msi
* Global installation:
    1. npx: `npm install -g npx`

### React latest version config:
* Create project: `npx create-react-app <project_name>`
* Configure TypeScript: `npm install --save typescript @types/node @types/react @types/react-dom @types/jest`
* Plugins:
    1. For API calls - axios: `npm install --save axios`
    2. For code format: `npm install prettier --save-dev`
        * Prettier allows you to set up a .prettierignore file right inside of the root of the project next to package.json, that allows you to tell Prettier what files it should not run on.
    3. For code debug: `npm install --save husky`
        * We can also add this config to our package.json to autoformat code on each git commit:
        ```json
        "scripts": {
            "lint": "prettier --check .",
            "format": "prettier --write ."
        },
        "husky": {
            "hooks": {
                "pre-commit": "echo \"[Husky] pre-commit\" && lint-staged"
            }
        },
        "lint-staged": {
            "*": "prettier --write"
        }
        ```
* Clean project vulnerabilities: `npm audit` and `npm audit fix`

## React with Next.js
### React with Next install:
* Create project & configure TypeScript: `npx create-next-app --typescript <project_name>`
* Plugins:
    1. For API calls - axios: `npm install --save axios`
    2. For code format: `npm install prettier --save-dev`
        * Prettier allows you to set up a .prettierignore file right inside of the root of the project next to package.json, that allows you to tell Prettier what files it should not run on.
    3. For code debug: `npm install --save husky`
        * We can also add this config to our package.json to autoformat code on each git commit:
        ```json
        "scripts": {
            "lint": "prettier --check .",
            "format": "prettier --write ."
        },
        "husky": {
            "hooks": {
                "pre-commit": "echo \"[Husky] pre-commit\" && lint-staged"
            }
        },
        "lint-staged": {
            "*": "prettier --write"
        }
        ```
* Clean project vulnerabilities: `npm audit` and `npm audit fix`

## Helper commands and utilities
* View react version: `npm view react version` and `npm view react-native version`
* Install Prettier as extension.