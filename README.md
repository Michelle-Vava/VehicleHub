# VehicleHub

One place to run your vehicles, whether that's your own car, the family's cars, or a small business fleet.

VehicleHub keeps every vehicle's maintenance history, upcoming services, costs and documents together, and shows who's driving what. It has three plans built on the same core:

| Plan | For | Highlights |
|------|-----|-----------|
| **Personal** | One person's own vehicles | Maintenance log, service reminders, fuel and cost tracking, document storage |
| **Family** | A household sharing vehicles | Members, who-drives-what, shared costs, reminders for everyone |
| **Business** | Small fleets (trades, delivery, landscaping) | Driver roles, assignments, cost reports per vehicle, CSV export |

**Status:** pivoting. This codebase started as **Service Connect**, a marketplace connecting vehicle owners with mechanics. The working parts (auth, vehicles, notifications, messaging, uploads, the NestJS + Prisma backend and the React frontend) are being reshaped into VehicleHub, and the marketplace parts (providers, quotes, jobs) are being removed. See [ROADMAP.md](ROADMAP.md).

All data in this repo is made up. No real drivers, vehicles or payment details.

---

## Built with

| Layer | Choice |
|-------|--------|
| Frontend | React 18, TypeScript, Vite, TailwindCSS, TanStack Router + Query, Zustand, React Hook Form |
| Backend | NestJS, Prisma, PostgreSQL, Swagger |
| Auth | Clerk |
| Payments | Stripe (test mode) |
| Uploads | Cloudinary |
| Email | Resend |
| API client | Orval (generated from the Swagger spec) |
| Tests | Jest (backend), Vitest + Testing Library (frontend) |
| Deployment | Docker + docker-compose |

---

## Project structure

```
backend/
├── prisma/          # Schema, migrations, seed data (fake users and vehicles)
└── src/
    ├── modules/     # Feature modules (auth, users, vehicles, notifications, messages, ...)
    ├── shared/      # Guards, filters, utilities
    └── main.ts      # App entry; API prefix /service-connect
frontend/
└── src/
    ├── features/    # auth, vehicles, owner, notifications, messages, settings, ...
    └── ...
docker-compose.yml   # Postgres + backend + frontend
```

---

## Running locally

**Requirements:** Node.js 18+, PostgreSQL (or Docker).

1. Install dependencies
   ```bash
   cd backend && npm install
   cd ../frontend && npm install
   ```

2. Set up environment files from the templates (placeholders only; use your own keys)
   ```bash
   cp backend/.env.example backend/.env
   cp frontend/.env.example frontend/.env.local
   ```

3. Create the database and run migrations
   ```bash
   cd backend
   npm run prisma:migrate
   npm run prisma:seed      # optional: fake sample data
   ```

4. Start both apps
   ```bash
   cd backend && npm run start:dev    # API on http://localhost:4201
   cd frontend && npm run dev         # web app on http://localhost:5173
   ```

Or run everything with Docker:
```bash
docker-compose up
```

## Tests

```bash
cd backend && npm test
cd frontend && npm test
```

---

## License

[MIT](LICENSE) © 2026 Michelle Vava
