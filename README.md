## Why
- easy to share code between packages
- easy to share dependencies
- faster builds (turbo repo)

## Intro 
```
.
├── package.json
├── README.md
├── packages → containing the component library package
└── apps     → containing the site to test the library
```


## Create new React Package
NOTE: This should be done with plop

1. `yarn create vite my-lib --template react-ts`
2. `yarn add --dev vite-plugin-dts`

```
import react from '@vitejs/plugin-react';
import path from 'node:path';
import { defineConfig } from 'vite';
import dts from 'vite-plugin-dts';

export default defineConfig({
    plugins: [
        react(),
        dts({
            insertTypesEntry: true,
        }),
    ],
    build: {
        lib: {
            entry: path.resolve(__dirname, 'src/lib/index.ts'),
            name: '<NAME OF LIB>',
            formats: ['es', 'umd'],
            fileName: (format) => `<NAME_OF_PACKAGE_DIR>.${format}.js`,
        },
        rollupOptions: {
            external: ['react', 'react-dom', 'styled-components'],
            output: {
                globals: {
                    react: 'React',
                    'react-dom': 'ReactDOM',
                    'styled-components': 'styled',
                },
            },
        },
    },
});
```

