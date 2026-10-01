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

- **Frontend:** React, Redux Toolkit, Tailwind CSS, React Router
- **Backend:** Node.js, Express, Sequelize ORM
- **Database:** PostgreSQL
- **Authentication:** JWT (JSON Web Tokens)
- **Payment Gateway:** Stripe/Razorpay
- **File Storage:** Multer for image uploads

## Project Structure

```
multi-vendor-ecommerce/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Buyer/
│   │   │   │   ├── ProductCard.jsx
│   │   │   │   ├── ProductDetails.jsx
│   │   │   │   ├── Cart.jsx
│   │   │   │   ├── Checkout.jsx
│   │   │   │   └── OrderHistory.jsx
│   │   │   ├── Seller/
│   │   │   │   ├── SellerDashboard.jsx
│   │   │   │   ├── ProductManagement.jsx
│   │   │   │   ├── OrderManagement.jsx
│   │   │   │   └── Analytics.jsx
│   │   │   ├── Admin/
│   │   │   │   ├── UserManagement.jsx
│   │   │   │   ├── SellerVerification.jsx
│   │   │   │   └── PlatformAnalytics.jsx
│   │   │   └── Common/
│   │   │       ├── Navbar.jsx
│   │   │       ├── Footer.jsx
│   │   │       └── AuthForm.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   └── NotFound.jsx
│   │   ├── redux/
│   │   │   ├── slices/
│   │   │   │   ├── authSlice.js
│   │   │   │   ├── cartSlice.js
│   │   │   │   └── productSlice.js
│   │   │   └── store.js
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   ├── authService.js
│   │   │   ├── productService.js
│   │   │   └── orderService.js
│   │   ├── hooks/
│   │   ├── utils/
│   │   ├── styles/
│   │   └── App.jsx
│   ├── .env.example
│   ├── package.json
│   └── vite.config.js
├── backend/
│   ├── config/
│   │   ├── database.js
│   │   └── env.js
│   ├── models/
│   │   ├── User.js
│   │   ├── Seller.js
│   │   ├── Product.js
│   │   ├── Order.js
│   │   ├── OrderItem.js
│   │   ├── Review.js
│   │   └── Wishlist.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── products.js
│   │   ├── orders.js
│   │   ├── sellers.js
│   │   └── admin.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── productController.js
│   │   ├── orderController.js
│   │   ├── sellerController.js
│   │   └── adminController.js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── errorHandler.js
│   ├── migrations/
│   │   └── initial.js
│   ├── .env.example
│   ├── package.json
│   └── server.js
└── README.md
```

## Database Schema (PostgreSQL)

### Users Table
- id (PK)
- email (unique)
- password (hashed)
- firstName
- lastName
- role (buyer, seller, admin)
- createdAt
- updatedAt

### Sellers Table
- id (PK)
- userId (FK)
- shopName
- shopDescription
- rating
- isVerified
- bankDetails
- createdAt

### Products Table
- id (PK)
- sellerId (FK)
- name
- description
- price
- stock
- category
- images
- rating
- createdAt
- updatedAt

### Orders Table
- id (PK)
- buyerId (FK)
- totalPrice
- status (pending, confirmed, shipped, delivered)
- shippingAddress
- createdAt
- updatedAt

### OrderItems Table
- id (PK)
- orderId (FK)
- productId (FK)
- quantity
- price

### Reviews Table
- id (PK)
- productId (FK)
- buyerId (FK)
- rating
- comment
- createdAt

### Wishlist Table
- id (PK)
- buyerId (FK)
- productId (FK)
- createdAt

## Getting Started

### Prerequisites
- Node.js (v14+)
- npm or yarn
- PostgreSQL (v12+)

### Installation

1. Clone the repository
   ```bash
   git clone https://github.com/hemu-7771/n.git
   cd n
   ```

2. **Backend Setup**
   ```bash
   cd backend
   npm install
   ```
   - Create `.env` file (copy from `.env.example`)
   - Configure PostgreSQL connection details
   - Run migrations: `npm run migrate`
   - Start server: `npm run dev`

3. **Frontend Setup**
   ```bash
   cd ../frontend
   npm install
   ```
   - Create `.env` file (copy from `.env.example`)
   - Configure API endpoint
   - Start dev server: `npm run dev`

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout

### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get product details
- `POST /api/products` - Create product (seller)
- `PUT /api/products/:id` - Update product (seller)
- `DELETE /api/products/:id` - Delete product (seller)

### Orders
- `GET /api/orders` - Get user orders
- `POST /api/orders` - Create order
- `GET /api/orders/:id` - Get order details
- `PUT /api/orders/:id` - Update order status (seller/admin)

### Sellers
- `GET /api/sellers/:id` - Get seller info
- `PUT /api/sellers/:id` - Update seller profile

### Admin
- `GET /api/admin/users` - Get all users
- `GET /api/admin/sellers` - Get all sellers
- `PUT /api/admin/sellers/:id/verify` - Verify seller

## Environment Variables

### Backend (.env)
```
DB_HOST=localhost
DB_PORT=5432
DB_NAME=ecommerce
DB_USER=postgres
DB_PASSWORD=password
JWT_SECRET=your_secret_key
NODE_ENV=development
PORT=5000
```

### Frontend (.env)
```
VITE_API_URL=http://localhost:5000/api
```

## License

MIT
