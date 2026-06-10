# 🧹 CleanPro Manager

A full-stack professional cleaning company management system built with **Next.js 14**, **Prisma**, **SQLite**, **Tailwind CSS**, and **NextAuth**.

---

## ✨ Features

| Module | Description |
|---|---|
| 🔐 Login | Secure authentication with NextAuth |
| 📊 Dashboard | KPIs, today's schedule, pending invoices, revenue chart |
| 📅 Schedule | Drag-and-drop weekly/bi-weekly/custom schedule |
| 👥 Clients | Full client CRM with search and filters |
| 🚗 Staff / Drivers | Employee management with color coding |
| 📋 Quotes | Quote lifecycle (pending → accepted / rejected) |
| 🧾 Invoices | Create, view, print-ready PDF invoices |
| 💳 Payments | Cash / Bank Transfer / TNG / DuitNow / Card |
| 💰 Expenses | Staff expense tracking with receipt upload |
| 📝 Daily Report | Drivers record cash received + photo upload |
| ⚙️ Settings | Language (EN/中文), company info, notifications |
| 📱 Mobile | Fully responsive with bottom nav + PWA manifest |

---

## 🚀 Quick Start

### 1. Install dependencies
```bash
npm install
```

### 2. Set up environment
```bash
cp .env.example .env.local
# Edit .env.local — defaults work for local dev
```

### 3. Set up database
```bash
npx prisma generate
npx prisma db push
npx ts-node --project tsconfig.json prisma/seed.ts
```

### 4. Start the dev server
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

**Demo credentials:**
- Email: `admin@cleanpro.com`
- Password: `admin123`

---

## 🗄️ Database

Uses **SQLite** (via Prisma) for local development. To switch to **PostgreSQL** for production:

1. Update `prisma/schema.prisma`:
```prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}
```

2. Update `DATABASE_URL` in `.env.local`:
```
DATABASE_URL="postgresql://user:password@localhost:5432/cleanpro"
```

3. Run:
```bash
npx prisma db push
npx ts-node prisma/seed.ts
```

---

## 🏗️ Project Structure

```
src/
├── app/
│   ├── (auth)/login/          # Login page
│   ├── (dashboard)/           # All authenticated pages
│   │   ├── dashboard/
│   │   ├── schedule/          # Drag-drop schedule
│   │   ├── clients/
│   │   ├── employees/
│   │   ├── quotes/
│   │   ├── invoices/
│   │   ├── payments/
│   │   ├── expenses/
│   │   ├── daily-report/
│   │   └── settings/
│   └── api/                   # REST API routes
│       ├── auth/
│       ├── clients/
│       ├── jobs/
│       ├── invoices/
│       ├── quotes/
│       ├── payments/
│       ├── expenses/
│       ├── reports/
│       └── settings/
├── components/
│   ├── layout/                # Sidebar, MobileNav, MobileHeader
│   ├── modals/                # All modal forms
│   ├── charts/                # Recharts components
│   └── ui/                    # Base UI (Toaster)
├── lib/
│   ├── auth.ts                # NextAuth config
│   ├── prisma.ts              # Prisma singleton
│   ├── i18n.ts                # EN/ZH translations
│   └── constants.ts           # Colors, options
└── store/
    └── languageStore.ts       # Zustand language state
prisma/
├── schema.prisma              # Full DB schema
└── seed.ts                    # Sample data seed
```

---

## 🚢 Deployment

### Vercel (recommended)
```bash
npm i -g vercel
vercel --prod
```
Set environment variables in Vercel dashboard.

### Docker
```dockerfile
FROM node:20-alpine
WORKDIR /app
COPY . .
RUN npm ci && npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

---

## 🌐 Languages

Switch between **English** and **中文** at any time via:
- Sidebar language button
- Settings → General → Language
- Login page buttons

---

## 📱 Mobile / PWA

The app works as a Progressive Web App. On mobile:
- Add to Home Screen for a native-like experience
- Bottom navigation bar for quick access
- Responsive layout for all screen sizes

---

## 🔑 Default Users

| Email | Password | Role |
|---|---|---|
| admin@cleanpro.com | admin123 | Admin (full access) |
| kay@cleanpro.com | kay123 | Supervisor |

---

## 📄 License

MIT — free to use and modify for your business.
