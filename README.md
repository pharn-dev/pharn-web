# pharn-web

A static Vercel deployment that redirects all traffic to the [`pharn-dev/pharn-oss`](https://github.com/pharn-dev/pharn-oss) repository.

## How it works

All routing lives in [`vercel.json`](./vercel.json). Every path is permanently redirected (HTTP 308) to the GitHub repository:

| Source    | Destination                              |
| --------- | ---------------------------------------- |
| `/`       | `https://github.com/pharn-dev/pharn-oss` |
| `/(.*)`   | `https://github.com/pharn-dev/pharn-oss` |

Because the redirects are permanent, browsers and search engines cache them. If you change the destination, clients may continue using the old target until their cache expires.

## Deployment

Deployed via [Vercel](https://vercel.com). There is no build step — Vercel reads `vercel.json` directly. Pushing to `main` triggers a deploy.

## License

[MIT](./LICENSE)
