# Contributing

Thanks for taking an interest in improving this grocery delivery project. This guide keeps local setup, commits, and pull requests consistent.

## Local Setup

Install dependencies separately for the backend and frontend:

```bash
cd server
npm install
npx prisma db push
npm run seed
npm run server
```

In another terminal:

```bash
cd client
npm install
npm run dev
```

## Branch Naming

Use short, descriptive branch names:

```text
feat/order-tracking
fix/cart-total
docs/setup-guide
chore/env-examples
```

## Commit Style

Prefer small commits with clear messages:

```text
feat: add delivery dashboard filters
fix: handle missing API base URL
docs: document environment variables
chore: update gitignore rules
```

## Before Opening A Pull Request

- Run the app locally.
- Confirm no `.env` files are staged.
- Keep commits focused on one purpose.
- Update documentation when setup or behavior changes.

## Security

Never commit real secrets, including:

- Database URLs
- JWT secrets
- Stripe keys
- Cloudinary credentials
- SMTP passwords
- Inngest keys

Use `.env.example` files to document required variables safely.
