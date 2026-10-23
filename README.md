# client-boundary

Keep client code out of server components

## Install

```bash
npm install client-boundary
```

## Usage

Add the import at the top of any module that must only run on the client.

```ts
import "client-boundary";

export const track = (event: string) => window.gtag?.("event", event);
```

If a Server Component imports this module, the build fails with a clear error.

## How it works

The package uses the `react-server` export condition, which Next.js sets only when bundling Server Components.

| Environment       | Resolves to      | Result                |
| ----------------- | ---------------- | --------------------- |
| Server Component  | `src/error.js`   | Throws a build error  |
| Client Component  | `src/index.js`   | No-op                 |

## Notes

- Zero dependencies
- Works with Next.js and any bundler that supports the `react-server` condition
- Pair it with [server-boundary](https://www.npmjs.com/package/server-boundary) for the opposite direction

## License

MIT
