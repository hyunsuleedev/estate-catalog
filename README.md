# Estait public property catalog

Map-first public property website extracted from `hyunsuleedev/estate-erp` (`3f739dc`).
The repository contains the consumer frontend only. NestJS APIs, migrations, and ERP workflows remain in the ERP repository.

## Development

```sh
pnpm install --frozen-lockfile
cp .env.example .env.local
pnpm dev
```

Open http://localhost:5180/demo for fictional listing data. Demo requests do not send data to brokers.
The default `/api` development proxy targets http://localhost:3000.

## Validation

```sh
pnpm lint
pnpm test
pnpm build
```

## Production configuration

Set `VITE_API_BASE_URL` to the deployed ERP API origin. `VITE_NAVER_MAPS_NCP_KEY_ID` and `VITE_CLERK_PUBLISHABLE_KEY` are public browser identifiers; never put server secrets in any `VITE_*` variable.
Configure allowed website origins in NAVER Maps, Clerk, and the server's `CATALOG_AUTH_ORIGINS`/CORS settings.
This Vite SPA needs host rewrites for `/demo`, `/homes/*`, and `/offices/*` to `index.html`.
Build command: `pnpm build`. Output directory: `dist`.

## Current limits

Map authentication and real consumer-to-ERP delivery still require environment verification. The existing request API is the initial implementation; the planned recipient inbox and worker architecture are not implemented yet.
No local credentials or production customer records are included intentionally. Public release remains subject to repository and history review.
