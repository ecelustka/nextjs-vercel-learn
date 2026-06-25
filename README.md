<div align="center">

# 🧾 Acme Dashboard

**A full‑stack invoicing dashboard built with the Next.js App Router.**

Authentication, server-side data mutations, search, pagination, streaming, and error handling — the complete [Next.js Learn](https://nextjs.org/learn) course app, fully implemented.

<p>
  <img alt="Next.js" src="https://img.shields.io/badge/Next.js-16-000000?logo=nextdotjs&logoColor=white" />
  <img alt="React" src="https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black" />
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-5.7-3178C6?logo=typescript&logoColor=white" />
  <img alt="Tailwind CSS" src="https://img.shields.io/badge/Tailwind-3.4-38BDF8?logo=tailwindcss&logoColor=white" />
  <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-Postgres.js-4169E1?logo=postgresql&logoColor=white" />
  <img alt="Auth.js" src="https://img.shields.io/badge/Auth.js-NextAuth%205-FF6F61" />
</p>

<img src="./public/hero-desktop.png" alt="Acme Dashboard preview" width="680" />

</div>

---

## 🔑 Demo login

Seed the database (see [Getting started](#-getting-started)), then sign in with:

| Field    | Value                |
| -------- | -------------------- |
| Email    | `user@nextmail.com`  |
| Password | `123456`             |

> [!NOTE]
> Passwords are hashed with **bcrypt** on seed. The plaintext above is for local/demo use only — never ship demo credentials to production.

---

## ✨ Features

- 🔐 **Authentication** — credentials provider via NextAuth (Auth.js v5), route protection in middleware (`proxy.ts`)
- 📊 **Dashboard overview** — revenue chart, latest invoices, summary cards with streaming + Suspense
- 🧾 **Invoice CRUD** — create, edit, delete invoices through React Server Actions
- 👥 **Customers** — searchable customer table
- 🔎 **Search & pagination** — URL-driven, debounced server-side search
- ⚡ **Streaming & loading UI** — `loading.tsx`, skeletons, partial rendering
- 🧯 **Error handling** — `error.tsx` boundaries + `not-found.tsx`
- ♿ **Accessibility** — server-side form validation with `useActionState`
- 🔍 **SEO** — per-page metadata, Open Graph image

---

## 🧱 Tech stack

| Layer       | Tech                                              |
| ----------- | ------------------------------------------------- |
| Framework   | Next.js (App Router, Server Components, Actions)  |
| Language    | TypeScript                                        |
| Styling     | Tailwind CSS + `@tailwindcss/forms`               |
| Database    | PostgreSQL via [`postgres`](https://github.com/porsager/postgres) (Postgres.js) |
| Auth        | NextAuth `5.0.0-beta` (Credentials) + bcrypt      |
| Validation  | Zod                                               |
| Icons       | Heroicons                                         |

---

## 🚀 Getting started

### Prerequisites

- **Node.js** 20+ (developed on v22)
- **pnpm** — `npm install -g pnpm`
- A **PostgreSQL** database (e.g. [Vercel Postgres](https://vercel.com/docs/storage/vercel-postgres) or local)

### 1. Install dependencies

```bash
pnpm install
```

### 2. Configure environment

Copy the example file and fill in your values:

```bash
cp .env.example .env.local
```

```dotenv
POSTGRES_URL=postgres://user:password@host:5432/dbname

# Generate with: openssl rand -base64 32
AUTH_SECRET=your-generated-secret
AUTH_URL=http://localhost:3000/api/auth
```

### 3. Seed the database

Start the dev server, then hit the seed route **once** to create tables and load demo data (users, customers, invoices, revenue):

```bash
pnpm dev
# then in a browser or curl:
curl http://localhost:3000/seed
```

### 4. Open the app

Visit **[http://localhost:3000](http://localhost:3000)** and log in with the [demo credentials](#-demo-login).

---

## 📜 Scripts

| Command       | Description                              |
| ------------- | ---------------------------------------- |
| `pnpm dev`    | Start dev server (Turbopack)             |
| `pnpm build`  | Production build                         |
| `pnpm start`  | Serve the production build               |
| `pnpm lint`   | Run ESLint                               |

---

## 🗂️ Project structure

```
app/
├── layout.tsx              # Root layout + metadata
├── page.tsx                # Landing page
├── login/                  # Login page
├── dashboard/              # Protected dashboard
│   ├── (overview)/         # Cards, charts, latest invoices
│   ├── invoices/           # Invoice list + create/edit/delete
│   └── customers/          # Customer table
├── lib/                    # data.ts, actions.ts, definitions.ts, utils.ts
├── ui/                     # Reusable components, fonts, global.css
└── seed/route.ts           # One-time DB seeding endpoint
auth.ts                     # NextAuth config + credential authorize
auth.config.ts              # Auth pages + route-protection callbacks
proxy.ts                    # Middleware: gates protected routes
```

---

## 📚 Learn more

Built following the official [Next.js App Router course](https://nextjs.org/learn/dashboard-app/getting-started). For framework details, see the [Next.js docs](https://nextjs.org/docs).

---

<div align="center">
<sub>Built with the Next.js App Router · deploy on <a href="https://vercel.com">Vercel</a></sub>
</div>
