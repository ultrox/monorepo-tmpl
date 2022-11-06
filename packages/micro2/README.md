## How it works

### Ingrediants:
- package name as folder name
- package.json with name value
- package.json main value

## Consumer
To use package you need to:
1. require it from it's package.json as a name of folder in /packages
2. import it in any of consumer file based on the name value in of package.json
3. Code that runs actually is defined by main value

### Example

This package lives in:
- `packages/micro2`
- name of this package is `boop`
- module `main` is pointing to `/bip/index.js`(this would be where is build files)

#### To use it
1. In `package.json`
```json
  "dependencies": {
    "micro2": "*",
	}
```

2. In code
```js
import {a} from "boop"
```

## Finally
If you changing names of any of `Ingrediants` you need to run `yarn install`
in consumers, to update sym link.
