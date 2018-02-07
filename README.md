# Custom THREE Build with Tree Shaking

This repo simply shows an example usage of [Matt DesLauriers's](https://github.com/mattdesl) treeshaking script for THREE.js, which you can read about [here](https://github.com/mattdesl/threejs-tree-shake).

If you look in `utils/` you'll find the script, `build_three.js`. This file imports `THREE` (via the node package), and overrides the `THREE` object, defining only the modules we want from it within it. Once built using Matt's scripts, we will have the file `build/three.custom.js` that defines a `window` level `THREE` object with only the modules we have requests (and the modules they themselves rely on from within `THREE`). You then just import the file however you would have imported the real `THREE` and it should "just work".

I am unsure if this is even wise. It's definitely a hack. However, this has allowed me to do things like release `Blotter.js` at a significantly lower build-size while still working fine using `THREE`. Your mileage may vary.


# Build

To run a build, change the contents of `utils/build_three.js` to bring in whatever `THREE` modules you need in your project, and then run the following NPM command:

```
$ npm run build-custom-three
```

The resulting file will be in `build/three.custom.js`.

