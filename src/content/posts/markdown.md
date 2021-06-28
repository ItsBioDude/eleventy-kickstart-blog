---
title: Markdown
img: https://images.unsplash.com/photo-1624385829865-b46466535995?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=810&q=80
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet. Duis sagittis ipsum. Praesent mauris. Fusce nec tellus sed augue semper porta. Mauris massa. Vestibulum lacinia arcu eget nulla. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Curabitur sodales ligula in libero. Sed dignissim lacinia nunc. Curabitur tortor. Pellentesque nibh. Aenean quam. In scelerisque sem at dolor. Maecenas mattis. Sed convallis tristique sem. Proin ut ligula vel nunc egestas porttitor. Morbi lectus risus, iaculis vel, suscipit quis, luctus non, massa. Fusce ac turpis quis ligula lacinia aliquet. Mauris ipsum. Nulla metus metus, ullamcorper vel, tincidunt sed, euismod in, nibh. Quisque volutpat condimentum velit. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Nam nec ante. Sed lacinia, urna non tincidunt mattis, tortor neque adipiscing diam, a cursus ipsum ante quis turpis. Nulla facilisi. Ut fringilla. Suspendisse potenti. Nunc feugiat mi a tellus consequat imperdiet. Vestibulum sapien. Proin quam. Etiam ultrices. Suspendisse in justo eu magna luctus suscipit. Sed lectus. Integer euismod lacus luctus magna. Quisque cursus, metus vitae pharetra auctor, sem massa mattis sem, at interdum magna augue eget diam. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Morbi lacinia molestie dui. Praesent blandit dolor. Sed non quam. In vel mi sit amet augue congue elementum. Morbi in ipsum sit amet pede facilisis laoreet. Donec lacus nunc, viverra nec, blandit vel, egestas et, augue. Vestibulum tincidunt malesuada tellus. Ut ultrices ultrices enim. Curabitur sit amet mauris. Morbi in dui quis est pulvinar ullamcorper.

```js
import { defineConfig } from 'vite';
import legacy from '@vitejs/plugin-legacy';
const isDev = process.env.NODE_ENV === 'development';
// https://vitejs.dev/config/
export default defineConfig({
    // This is not critical, but I include it because there are more HTML transforms via plugins, that templates must handle
    // TODO: For legacy() to work without a hitch, we set a known @babel/standalone version in package.json
    // Remove that once https://github.com/vitejs/vite/issues/2442 is fixed
    plugins: [legacy()],
    publicDir: 'static',
    base: '/',
    build: {
        // This is important: Generate directly to website and then assetsDir.
        // You could opt to build in an intermediate directory,
        // and have Eleventy copy the flies instead.
        outDir: 'website',
        // This is the default assetsDir. If you are using assets
        // for anything else, consider renaming assetsDir.
        // This can help you set cache headers for hashed output more easily.
        // assetsDir: "assets",
        // Sourcemaps are nice, but not critical for this to work
        sourcemap: isDev,
        // This is critical: generate manifest.json in outDir
        manifest: true,
        rollupOptions: {
            // This is critical: overwrite default .html entry
            input: '/src/index.js',
        },
        terserOptions: { ecma: '5' },
    },
});
```