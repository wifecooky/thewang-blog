---
slug: docusaurus-update-to-v3
title: Update Docusaurus to v3
description: Update Docusaurus to v3
authors: [wifecooky]
tags: [docusaurus]
keywords: [docusaurus]
image: "https://docusaurus.io/img/docusaurus_keytar.svg"
---

## Update Docusaurus to v3

[Docuaurus v3](https://docusaurus.io/blog/releases/3.0) has been released, here is the [migration guide](https://docusaurus.io/docs/migration/v3) provided by the official.

I record the upgrade process here that may help you save some time. 😄

### Upgrade dependencies

- docusaurus.config.js

```js title="docusaurus.config.js"

-const lightCodeTheme = require('prism-react-renderer/themes/github');
-const darkCodeTheme = require('prism-react-renderer/themes/dracula');
+const { themes } = require('prism-react-renderer');
+const lightTheme = themes.github;
+const darkTheme = themes.dracula;

       prism: {
-        theme: lightCodeTheme,
-        darkTheme: darkCodeTheme,
+        theme: lightTheme,
+        darkTheme: darkTheme,
       },

```

- package.json

```json title="package.json"
   "dependencies": {
-    "@docusaurus/core": "2.4.3",
-    "@docusaurus/preset-classic": "2.4.3",
-    "@docusaurus/theme-mermaid": "^2.4.3",
-    "@mdx-js/react": "^1.6.22",
+    "@docusaurus/core": "3.0.0",
+    "@docusaurus/preset-classic": "3.0.0",
+    "@docusaurus/theme-mermaid": "^3.0.0",
+    "@mdx-js/react": "^3.0.0",
     "clsx": "^1.2.1",
-    "prism-react-renderer": "^1.3.5",
-    "react": "^17.0.2",
-    "react-dom": "^17.0.2"
+    "prism-react-renderer": "^2.1.0",
+    "react": "^18.2.0",
+    "react-dom": "^18.2.0"
   },
   "devDependencies": {
-    "@docusaurus/module-type-aliases": "2.4.3"
+    "@docusaurus/module-type-aliases": "3.0.0",
+    "@docusaurus/types": "3.0.0"
   },


   "engines": {
-    "node": ">=16.14"
+    "node": ">=18.0"
   }

```

### Reinstall dependencies

Remove the `node_modules` directory and `package-lock.json` file, then reinstall the dependencies.

```bash
npm install
```

### Check if mx/mdx files compiles under MDX v3

Use the following command to check if mx/mdx files compiles under MDX v3.

```bash
npx docusaurus-mdx-checker
```

For example, I got a check error after upgrated to v3:

- Before Modified

```md
<details><summary>xxx</summary>
...
</details>
```

- After Modified

```md
<details>
<summary>xxx</summary>
...
</details>
```
