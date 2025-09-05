# Ecommerce Platform Slice

This is a production-grade slice of a multivendor ecommerce platform built with Next.js.

## Technologies

- React v19.1
- Next.js v15.3.5
- TypeScript v5.8
- Tailwind CSS v4.1
- CSS Grid and Flexbox
- Next.js API Routes
- Prisma (SQLite for local, PostgreSQL for prod)
- NextAuth.js (Credentials provider)
- Bcryptjs for password hashing

Justifications:

- Database: Prisma for type-safe ORM, SQLite for easy local setup (swap to PostgreSQL via DATABASE_URL for prod).
- Auth: NextAuth for seamless Next.js integration, Credentials for simple email/password (extendable to OAuth).
- Images: Placeholder URLs from Unsplash; in prod, use AWS S3 with signed URLs.
- No realtime: Optional, skipped for core focus.

## Setup Locally

1. Clone repo: `git clone <repo-url>`
2. Install deps: `npm install`
3. Copy `.env.example` to `.env` and fill values (e.g., DATABASE_URL=prisma/sqlite.db, NEXTAUTH_SECRET=random-string)
4. Setup DB: `npx prisma generate && npx prisma db push`
5. Seed data: `npx ts-node seed.ts`
6. Run dev: `npm run dev`[](http://localhost:3000)

Scripts:

- `npm run dev`: Development server
- `npm run build`: Build for prod
- `npm run start`: Start prod server
- `npm run lint`: Lint code
- `npm run test`: Run tests

## Deployment

Deploy to Vercel:

1. Push to GitHub.
2. Connect repo to Vercel dashboard.
3. Add env vars: DATABASE_URL (use PostgreSQL provider like Supabase), NEXTAUTH_SECRET, NEXTAUTH_URL=https://your-domain.com
4. Deploy. App is responsive across devices.

Demo URL: [Submit your deployed URL here]

## Demo Video

[Link to 3-6 min screencast showing flows: signup, explore, add to cart, checkout, order view]

## Tests

Unit tests for cart/order logic using Jest. Run `npm run test`.

Decisions/Trade-offs:

- Used app router for server components (performance).
- JSON for cart items (simplicity over relations).
- Modals not used; separate auth pages for clarity.
- Strict TypeScript for safety.
