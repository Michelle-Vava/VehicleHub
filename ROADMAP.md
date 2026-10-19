# VehicleHub Roadmap

VehicleHub started as Service Connect, a mechanic marketplace. This roadmap turns it into a vehicle management app for individuals, families and small fleets. All development uses made-up drivers, vehicles and payments (Stripe test mode).

## Already built (from Service Connect)
- [x] Clerk auth with roles, guards and auth tests
- [x] Vehicle CRUD, with photo uploads via Cloudinary
- [x] Notifications and messaging
- [x] NestJS + Prisma backend with Swagger and an Orval-generated frontend API client
- [x] Docker setup for Postgres, backend and frontend

## Phase 0: Pivot clean-up
- [ ] Remove marketplace modules: provider profiles, service requests, quotes, jobs, parts
- [ ] Remove provider sign-up and provider screens from the frontend
- [ ] Rename the API prefix from `/service-connect` to `/api`, app name and branding to VehicleHub
- [ ] Update the seed script to fake households, fleets and vehicles
- [ ] Regenerate the Orval client after the API changes

## Phase 1: Garages, members and roles
- [ ] `Garage` model: personal, family or business
- [ ] Members with roles: owner, manager, driver
- [ ] Invite members by email (Resend)
- [ ] Switch between garages if you belong to more than one
- [ ] Permission checks on every endpoint (drivers only see their assigned vehicles)

## Phase 2: Maintenance
- [ ] Maintenance records: date, odometer, service type, cost, notes, receipt photo
- [ ] Service schedules by time or distance (oil every 8,000 km, tire swap every spring)
- [ ] Due-soon and overdue reminders (in-app and email)
- [ ] Odometer updates from drivers

## Phase 3: Costs and fuel
- [ ] Fuel log: litres, price, odometer, with automatic L/100 km
- [ ] Expenses: insurance, registration, parking, tolls, repairs
- [ ] Cost per vehicle, per month and per km
- [ ] Charts on the dashboard

## Phase 4: Drivers and assignments (Family and Business)
- [ ] Assign vehicles to drivers, with date ranges
- [ ] Vehicle availability calendar
- [ ] Simple check-out / check-in with odometer and condition notes

## Phase 5: Documents
- [ ] Upload insurance, registration and inspection documents per vehicle
- [ ] Expiry dates with reminders before they lapse

## Phase 6: Plans and billing
- [ ] Personal (free), Family and Business plans with vehicle and member limits
- [ ] Stripe subscriptions in test mode, with webhooks
- [ ] Upgrade prompts when a limit is reached

## Phase 7: Polish and release
- [ ] Dashboard: what's due, what's overdue, this month's costs
- [ ] CSV export of maintenance and costs (Business)
- [ ] Mobile-friendly layouts for drivers
- [ ] More backend and frontend tests; GitHub Actions CI
- [ ] Deploy with Docker
