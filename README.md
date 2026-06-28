# Grocery Delivery Full Stack

A modern full-stack grocery delivery platform inspired by quick-commerce experiences. The app includes a customer storefront, cart and checkout flow, order tracking, an admin dashboard, product management, delivery partner management, and delivery partner order handling.

> Built as a production-style MERN-adjacent application with React, TypeScript, Express, Prisma, Neon PostgreSQL, Stripe, Cloudinary, Inngest, and email notifications.

## Demo URL

Live demo: https://grocery-app-full-stack-9l4n.vercel.app/

## Highlights

- Customer storefront with categories, product listing, search, flash deals, product detail pages, and cart
- Authentication with JWT-based protected routes
- Address management and multi-step checkout
- Stripe-ready payment flow and webhook endpoint
- Order history and live order tracking UI
- Admin dashboard for products, orders, stats, and delivery partners
- Delivery partner login and delivery workflow
- Product image upload support through Cloudinary
- Background/event workflow support through Inngest
- Email notification support through SMTP/Brevo
- PostgreSQL data layer powered by Prisma and Neon

## Tech Stack

**Frontend**

- React 19
- TypeScript
- Vite
- React Router
- Axios
- Tailwind CSS
- React Leaflet
- Lucide React

**Backend**

- Node.js
- Express 5
- TypeScript
- Prisma 7
- Neon PostgreSQL
- JWT authentication
- Stripe
- Cloudinary
- Nodemailer / Brevo SMTP
- Inngest

## Project Structure

```text
grocery-delivery-fullstack/
├── client/                 # React + Vite frontend
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── context/        # Auth and cart state
│   │   ├── pages/          # Customer, admin, and delivery pages
│   │   └── config/         # API client config
│   └── package.json
├── server/                 # Express + Prisma backend
│   ├── controllers/        # Route handlers
│   ├── middleware/         # Auth and role middleware
│   ├── prisma/             # Prisma schema
│   ├── routes/             # API routes
│   ├── inngest/            # Background functions
│   ├── seed.ts             # Product seed script
│   └── package.json
└── README.md
```

## Getting Started

### Prerequisites

Install these before running the project:

- Node.js 20 or newer
- npm
- A Neon PostgreSQL database
- Optional service accounts for Cloudinary, Stripe, Brevo/SMTP, and Inngest

### 1. Clone The Repository

```bash
git clone https://github.com/YOUR_USERNAME/grocery-delivery-fullstack.git
cd grocery-delivery-fullstack
```

If you are already inside the local project folder, use:

```bash
cd /home/kushagra/Desktop/Grocery-delivery-full-stack-instacart/grocery-delivery-fullstack
```

### 2. Configure Environment Variables

Create backend environment file:

```bash
cp server/.env.example server/.env
```

Update `server/.env`:

```env
PORT=5000
CLIENT_URL=http://localhost:5173
JWT_SECRET=replace-with-a-long-random-secret
ADMIN_EMAILS=admin@example.com
DATABASE_URL=postgresql://USER:PASSWORD@HOST/neondb?sslmode=require

CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=

INNGEST_EVENT_KEY=
INNGEST_SIGNING_KEY=

SENDER_EMAIL=
SMTP_USER=
SMTP_PASS=

STRIPE_SECRET_KEY=
STRIPE_WEBHOOK_SECRET=
```

Create frontend environment file:

```bash
cp client/.env.example client/.env
```

For local development, `client/.env` should contain:

```env
VITE_CURRENCY_SYMBOL="$"
VITE_BASE_URL=http://localhost:5000/api
```

### 3. Install Backend Dependencies

```bash
cd server
npm install
```

### 4. Sync Database Schema

```bash
npx prisma db push
```

### 5. Seed Products

```bash
npm run seed
```

This adds sample grocery products to the database.

### 6. Start Backend

```bash
npm run server
```

The API should be available at:

```text
http://localhost:5000
```

### 7. Install Frontend Dependencies

Open a second terminal:

```bash
cd client
npm install
```

### 8. Start Frontend

```bash
npm run dev
```

The frontend should be available at:

```text
http://localhost:5173
```

## Useful Scripts

### Backend

```bash
npm run server   # Start backend with nodemon
npm run start    # Start backend with tsx
npm run seed     # Seed database with products
npm run build    # Compile TypeScript
```

### Frontend

```bash
npm run dev      # Start Vite dev server
npm run build    # Build production frontend
npm run preview  # Preview production build
npm run lint     # Run ESLint
```

## Main Routes

### Customer

- `/` - Home
- `/products` - Product listing
- `/products/:id` - Product details
- `/search` - Search results
- `/deals` - Flash deals
- `/checkout` - Checkout
- `/orders` - My orders
- `/orders/:id` - Order tracking
- `/addresses` - Saved addresses

### Admin

- `/admin` - Admin dashboard
- `/admin/products` - Product management
- `/admin/products/new` - Add product
- `/admin/orders` - Order management
- `/admin/delivery-partners` - Delivery partner management

### Delivery Partner

- `/delivery/login` - Delivery partner login
- `/delivery` - Delivery dashboard

## API Overview

Backend API base URL:

```text
http://localhost:5000/api
```

Available route groups:

- `/api/auth`
- `/api/products`
- `/api/upload`
- `/api/orders`
- `/api/addresses`
- `/api/admin`
- `/api/delivery`
- `/api/inngest`
- `/api/stripe`

## Security Notes

- Never commit real `.env` files.
- Keep `DATABASE_URL`, `JWT_SECRET`, Stripe keys, Cloudinary keys, SMTP credentials, and Inngest keys private.
- Use `.env.example` files to document required variables without exposing secrets.
- Rotate any secret immediately if it was pushed publicly by mistake.
- Use strong, unique values for `JWT_SECRET` in production.

## Deployment Notes

Recommended deployment setup:

- Frontend: Vercel
- Backend: Vercel, Render, Railway, or another Node-compatible host
- Database: Neon PostgreSQL
- File uploads: Cloudinary
- Payments: Stripe
- Background jobs: Inngest
- Email: Brevo SMTP

For production, update:

```env
CLIENT_URL=https://your-client-domain.com
VITE_BASE_URL=https://your-server-domain.com/api
```

Also configure Stripe webhook endpoint and Inngest sync URL using your deployed backend URL.

## Author

Created by Kushagra.

## License

This project is available for learning, portfolio, and personal development use.
