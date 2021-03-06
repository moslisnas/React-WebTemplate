# React-WebTemplate
React web project templates.

This project can be used to generate your own applications.

Actually available:
* React v17.0.2 - latest version at 11/07/2021
* React v17.0.2 with Next.js - latest version at 11/07/2021

### React global install:
1. We install node from this link: https://nodejs.org/dist
2. npx package let us build a React project easily:
```
npm install -g npx
```

## React latest version
### React latest version config:
* Create project: 
    ```
    npx create-react-app <project_name>
    ```
* Configure TypeScript: 
    ```
    npm install --save typescript @types/node @types/react @types/react-dom @types/jest
    ```
* Plugins:
    1. For API calls - axios: 
    ```
    npm install --save axios
    ```
    2. For code format:
        ```
        npm install prettier --save-dev
        ```
        * Prettier allows you to set up a .prettierignore file right inside of the root of the project next to package.json, that allows you to tell Prettier what files it should not run on.
    3. For code debug:
        ```
        npm install --save husky
        npm install eslint eslint-plugin-react --save-dev
        ```
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
        * Same for es-lint:
            * .eslintrc:
            ```json
            "extends": [
                "eslint:recommended",
                "plugin:react/recommended"
            ]
            ```
            * package.json:
            ```json
            "scripts": {
                "lint": "eslint src/**/*.js src/**/*.jsx src/**/*.ts src/**/*.tsx"
            }
            ```
* Clean project vulnerabilities:
    ```
    npm audit
    npm audit fix
    ```

## React with Next.js
### React with Next config:
* Create project & configure TypeScript:
    ```
    npx create-next-app --typescript <project_name>
    ```
* Plugins:
    1. For code format:
        ```
        npm install prettier --save-dev
        ```
        * Prettier allows you to set up a .prettierignore file right inside of the root of the project next to package.json, that allows you to tell Prettier what files it should not run on.
    2. For code debug:
        ```
        npm install --save husky
        npm install eslint eslint-plugin-react --save-dev
        ```
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
        * Same for es-lint:
            * .eslintrc:
                ```json
                "extends": [
                    "eslint:recommended",
                    "plugin:react/recommended"
                ]
                ```
            * package.json:
                ```json
                "scripts": {
                    "lint": "eslint ./**/*.ts ./**/*.tsx"
                }
                ```
    3. Optionals:
        * For API calls - axios:
            ```
            npm install --save axios
            ```
        * CSS and styling:
            1. Styled-components:
                ```
                npm install --save styled-components
                npm install --save-dev @types/styled-components
                ```
                To avoid the lost of CSS styles on every refresh you need to add the "_document.js" file inside pages folder with this content (https://github.com/vercel/next.js/blob/main/examples/with-styled-components/pages/_document.js):

                ```typescript
                import Document from 'next/document'
                import { ServerStyleSheet } from 'styled-components'

                export default class MyDocument extends Document {
                    static async getInitialProps(ctx) {
                        const sheet = new ServerStyleSheet()
                        const originalRenderPage = ctx.renderPage

                        try {
                            ctx.renderPage = () =>
                            originalRenderPage({
                            enhanceApp: (App) => (props) =>
                                sheet.collectStyles(<App {...props} />),
                            });

                            const initialProps = await Document.getInitialProps(ctx);
                            return {
                                ...initialProps,
                                styles: (
                                <>
                                    {initialProps.styles}
                                    {sheet.getStyleElement()}
                                </>
                                ),
                            }
                        }
                        finally {
                            sheet.seal()
                        }
                    }
                }
                ```
                To avoid console warnings on className of styled-components elements we need to add in the project main folder the ".babelrc" file with this content:
                ```json
                {
                    "presets": ["next/babel"],
                    "plugins": [["styled-components", { "ssr": true }]]
                }
                ```

            2. Tailwind:
                ```
                npm install --save tailwindcss
                ```
        * Session (PENDING):
            ```
            npm install --save ?
            ```
* Additional util configuration:
    1. Reduce import statements to a base path, change tsconfig.json:
        * Specify base URL:
            ```json
            {
                "compilerOptions": {
                    ...
                    "baseUrl": "."
                }
            }
            ```
        * Reduce imports for a specific directory:
            ```json
            {
                "compilerOptions": {
                    ...
                    "paths": {
                        "@/components/*": ["components/*"],
                        "@/styles/*": ["styles/*"]
                    }
                }
            }
            ```


### React with Next run and utils commands:
* Run project:
    ```
    npm run dev
    ```
* Clean project vulnerabilities:
    ```
    npm audit
    npm audit fix
    ```

## Helper commands and utilities
* View react version:
    ```
    npm view react version
    npm view react-native version
    ```
* At Visual Studio Code - install Prettier as extension.