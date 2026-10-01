# Multi-Vendor E-Commerce Platform

A full-featured e-commerce platform built with React that enables multiple sellers to manage their products and buyers to purchase from various vendors.

## Features

### Buyer Features
- Browse products from multiple sellers
- Search and filter products
- Add products to cart
- Place orders
- Order tracking
- User profile management
- Wishlist functionality
- Product reviews and ratings

### Seller Features
- Seller dashboard
- Product management (add, edit, delete)
- Inventory management
- Order management
- Sales analytics
- Seller profile and ratings
- Payment settlement

### Admin Features
- User management
- Seller verification
- Order management
- Platform analytics
- Commission management

## Tech Stack

- **Frontend:** React, Redux, Tailwind CSS
- **Backend:** Node.js, Express
- **Database:** MongoDB
- **Authentication:** JWT
- **Payment Gateway:** Stripe/Razorpay

## Project Structure

```
multi-vendor-ecommerce/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Buyer/
│   │   │   ├── Seller/
│   │   │   ├── Admin/
│   │   │   └── Common/
│   │   ├── pages/
│   │   ├── redux/
│   │   ├── services/
│   │   ├── styles/
│   │   └── App.jsx
│   └── package.json
├── backend/
│   ├── routes/
│   │   ├── auth.js
│   │   ├── products.js
│   │   ├── orders.js
│   │   └── sellers.js
│   ├── models/
│   ├── middleware/
│   ├── controllers/
│   └── server.js
└── README.md
```

## Getting Started

### Prerequisites
- Node.js (v14+)
- npm or yarn
- MongoDB

### Installation

1. Clone the repository
2. Install frontend dependencies: `npm install` in `/frontend`
3. Install backend dependencies: `npm install` in `/backend`
4. Configure environment variables
5. Run the application

## License

MIT
