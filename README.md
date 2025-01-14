# Next 13 with Preact

![](https://media3.giphy.com/media/s239QJIh56sRW/giphy.gif)

_...Sighs in JavaScript..._

If you're unable to use the `app` directory with React Server Components (in beta), streaming SSR, or Suspense, but still want/need improvements to Next utilities, Next 13 with Preact is for you.

> Next 13 requires Preact to add support for [`renderToReadableStream`](https://github.com/preactjs/preact-render-to-string/pull/259).

## ⚠️ Disclaimer ⚠️

My approach was to achieve this with the least amount of changes to Next.js pointing back to Next 12.3.4. So I can't promise that this will work for all your use cases. I also can't promise that this will automatically work in future versions. Proceed with caution.

## Supported Next.js version
13.1.*

## Dependencies

- [next-preact-plugin](https://github.com/preactjs/next-plugin-preact)
- [patch-package](https://github.com/ds300/patch-package)
- [use-sync-external-store](https://www.npmjs.com/package/use-sync-external-store)

## Usage

Follow the instructions in [next-preact-plugin](https://github.com/preactjs/next-plugin-preact)

Run `patch-package` in `postinstall`:

```json
{
  "scripts": {
    "postinstall": "patch-package"
  }
}
```
## Patches

- Remove the check for React 18 in `next/dist/build/webpack-config.js`
- Switch back to `renderToString` in `next/dist/server/render.js`
- Dynamic imports without `lazy` in `next/dist/shared/lib/loadable.js`
  - Prevent running `ssr: false` loaders in `next/dist/shared/lib/dynamic.js`