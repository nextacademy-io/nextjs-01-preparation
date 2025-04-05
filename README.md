# Next.js Workshop: Preperation

In this task we'd like to install the required tools and setup a basic project for our needs.

## 1. Install Git

Go to https://git-scm.com/book/en/v2/Getting-Started-Installing-Git and install Git for your operating system.

## 2. Install Node.js and npm

Got to https://nodejs.org/en/download and install the most recent version of Node.js and npm (bundled). 

> [!TIP]
> Prefer to use the installation with [nvm](https://github.com/nvm-sh/nvm) on operating systems that support it (Linux, MacOS, ...).

## 3. Install your IDE: Visual Studio Code (VS Code)

Go to https://code.visualstudio.com and install the most recent version of _Visual Studio Code_ for your Operating System.

### 3.1. Recommended Extensions

- [ESLint extension](https://marketplace.visualstudio.com/items/?itemName=dbaeumer.vscode-eslint)
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
- [Apollo GraphQL for VS Code](https://marketplace.visualstudio.com/items?itemName=apollographql.vscode-apollo)

> [!NOTE]  
> Make sure to read the documentation of each extension. Some of them need to be configured to work properly.

## 4. Create the _clash_ project

We would like to setup a basic application, using the [Automatic installation](https://nextjs.org/docs/app/getting-started/installation#automatic-installation) approach:

```npx create-next-app@latest```

Follow this session:

✔ What is your project named? … **clash**

✔ Would you like to use TypeScript? … No / **Yes**

✔ Would you like to use ESLint? … No / **Yes**

✔ Would you like to use Tailwind CSS? … No / **Yes**

✔ Would you like your code inside a `src/` directory? … No / **Yes**

✔ Would you like to use App Router? (recommended) … No / **Yes**

✔ Would you like to use Turbopack for `next dev`? … No / **Yes**

✔ Would you like to customize the import alias (`@/*` by default)? … **No** / Yes

## 5. Configure auto formatting (on save) and Tailwind CSS autocomplete:

1. Create a file `.vscode/settings.json` in your project root, with the following content:

```json
{
  "files.associations": {
    "*.css": "tailwindcss"
  },
  "editor.quickSuggestions": {
    "strings": "on"
  },
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true
}
```

2. Create a file `.prettierrc` in your project root, with the following content:

```json
{
  "semi": true,
  "trailingComma": "all",
  "singleQuote": true,
  "printWidth": 100,
  "tabWidth": 2
}
```

> [!NOTE]  
> You might want to restart VS Code to make the changes work.

## 6. Setup shadcn/ui

```npx shadcn@latest init```

> [!NOTE]
> In case of issues, use the `--force` option

## 7. Project cleanup

Cleanup you're `app/page.tsx` by replacing its contents:

```tsx
export default function Home() {
  return (
    <div className="p-24">
      <h1 className="text-3xl font-bold underline">Hello, Workshop</h1>
    </div>
  );
}
```

## 8. Testing setup

Follow the instructions as described here: [Setting up Vitest with Next.js - Manual Setup](https://nextjs.org/docs/app/building-your-application/testing/vitest#manual-setup)

## 9. Debugging setup

Familarize yourself with the debbugging suggestions: https://nextjs.org/docs/app/building-your-application/configuring/debugging

Choose the right option for you.







