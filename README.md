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
    <main className="p-24">
      <h1 className="text-3xl font-bold underline">Hello, Workshop</h1>
    </main>
  );
}
```

## 8. Testing setup

8.1. Follow the instructions as described here: [Setting up Vitest with Next.js - Manual Setup](https://nextjs.org/docs/app/building-your-application/testing/vitest#manual-setup)

8.2. Place the file `app/page.test.psx` with the following content, next to `app/page.tsx`:

```tsx
import { expect, test } from 'vitest';
import { render, screen, within } from '@testing-library/react';
import Home from './page';

test('Home Page', () => {
  render(<Home />);
  const main = within(screen.getByRole('main'));
  expect(main.getByRole('heading', { level: 1, name: /Hello, Workshop/i })).toBeDefined();
});
```

8.3. Run `npm run test` to see the results:

```
% npm run test

> clash@0.1.0 test
> vitest


 DEV  v3.1.1 /Users/pawel/nextacademy-workshops/clash

 ✓ src/app/page.test.tsx (1 test) 26ms
   ✓ Home Page 25ms

 Test Files  1 passed (1)
      Tests  1 passed (1)
   Start at  15:04:23
   Duration  356ms (transform 17ms, setup 0ms, collect 61ms, tests 26ms, environment 146ms, prepare 24ms)

 PASS  Waiting for file changes...
       press h to show help, press q to quit
```
8.4. We'd like to use the popular [@testing-library/jest-dom](https://github.com/testing-library/jest-dom) library.

Run ```npm install --save-dev @testing-library/jest-dom```.

Create a `vitest.setup.ts` with the following content:

```ts
import { afterEach } from 'vitest';
import '@testing-library/jest-dom/vitest';
import { cleanup } from '@testing-library/react';

afterEach(() => {
  cleanup();
});
```

Update your `vitest.config.mts`:

```ts
import { defineConfig } from 'vitest/config';
import react from '@vitejs/plugin-react';
import tsconfigPaths from 'vite-tsconfig-paths';

export default defineConfig({
  plugins: [tsconfigPaths(), react()],
  test: {
    environment: 'jsdom',
    setupFiles: './vitest.setup.ts',
  },
});
```

8.5. We'd like to use [user-event](https://testing-library.com/docs/user-event/intro) library, for simulating user interaction

```sh
npm install --save-dev @testing-library/user-event
```

## 9. Debugging setup

Familarize yourself with the debbugging suggestions: https://nextjs.org/docs/app/building-your-application/configuring/debugging

Choose the right option for you.







