<h1 align="center">Athan</h1>

<p align="center">A desktop application created using ReactJS, TypeScript, CSS / SASS modules, Electron Vite, Eslint, Prettier, <strong>GitHub Action releases</strong> and more.
  <br/>
    <small align="center">Special Thanks to <a href="https://github.com/daltonmenezes/electron-app">@daltonmenezes</a></small>
  <br/><br/>
  <!-- Version -->
  <a href="https://github.com/bo3ouf/athan/releases">
     <img alt="releases url" src="https://img.shields.io/github/v/release/bo3ouf/athan?style=for-the-badge&labelColor=1C1E26&color=99EDC3"/>
  </a>  
  <!-- License -->
  <a href="https://github.com/bo3ouf/athan/blob/main/LICENSE">
    <img alt="license url" src="https://img.shields.io/badge/license%20-MIT-1C1E26?style=for-the-badge&labelColor=1C1E26&color=99EDC3"/>
  </a>
</p>

# Technologies

- 🔋 Electron
- 🔥 ReactJS
- 🌎 React Router DOM and Electron Router DOM
- 🧐 React Developer Tools
- 💙 TypeScript
- 📦 Electron Vite
- ✨ CSS / SASS modules
- 💫 Eslint / Prettier / EditorConfig / Husky / lint-staged / Commitlint
- 📦 Electron Builder
- 🔮 action-electron-builder

# Usage

First, install the dependencies by running on the terminal:

```
yarn
```

That done, just run the project with the following command:

```
yarn dev
```

Now, look at the **package.json** file in the root directory, you should update some of that settings with your project branding.

# Distribution

### For all platforms

> **Note**: Check [Electron Builder docs](https://www.electron.build/cli) for more knowledge

```
yarn build
```

### For a specific one

```bash
yarn build --mac
# OR
yarn build --win
# OR
yarn build --linux
```

The builded apps will be available on the `dist` folder.

# Source Code Protection

> This process is done via [v8 bytecode compilation](https://nodejs.org/api/vm.html#vm_script_createcacheddata), to get more knowledge about it, please, [check the Electron Vite docs](https://evite.netlify.app/guide/source-code-protection.html).

Use the `bytecodePlugin` from `electron-vite` to enable it in the **electron.vite.config.ts**:

```ts
import { defineConfig, bytecodePlugin } from "electron-vite";

export default defineConfig({
  main: {
    plugins: [tsconfigPaths, bytecodePlugin()],
  },

  preload: {
    // Note: you will get the following warning using bytecodePlugin in the preload script in production build: "The vm module of Node.js is deprecated in the renderer process and will be removed", is up to you to keep bytecodePlugin here. Also, keep following the Electron Vite docs for more updates about this plugin!
    plugins: [tsconfigPaths, bytecodePlugin()],
  },

  renderer: {
    // ...
  },
});
```

Also, `sandbox` should be `false` in `webPreferences` for the windows you are using a preload script like:

```ts
const window = createWindow({
  id: "main",

  webPreferences: {
    preload: join(__dirname, "../preload/index.js"),
    sandbox: false,
  },
});
```

# Contributing

> **Note**: contributions are always welcome, but always **ask first**, — please — before work on a PR.

# License

[MIT © Abdulrahman Alblooshi](https://github.com/bo3ouf/athan/blob/main/LICENSE)
