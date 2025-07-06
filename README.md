# 🍕 Food Delivery App

[![Node.js](https://img.shields.io/badge/Node.js-18.x-green?style=for-the-badge&logo=node.js)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18.3.1-blue?style=for-the-badge&logo=react)](https://reactjs.org/)
[![Express.js](https://img.shields.io/badge/Express.js-4.19.2-lightgrey?style=for-the-badge&logo=express)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-8.4.4-green?style=for-the-badge&logo=mongodb)](https://www.mongodb.com/)
[![Stripe](https://img.shields.io/badge/Stripe-16.1.0-purple?style=for-the-badge&logo=stripe)](https://stripe.com/)
[![Vite](https://img.shields.io/badge/Vite-5.3.1-646CFF?style=for-the-badge&logo=vite)](https://vitejs.dev/)

> A full-stack food delivery application built with the MERN stack, featuring real-time order management, secure payment processing, and comprehensive admin controls.

## ✨ Features

### 🛍️ Customer Features
- **Browse Menu** - Explore food categories and items with detailed descriptions
- **Shopping Cart** - Add/remove items with quantity management
- **User Authentication** - Secure login and registration with JWT
- **Order Placement** - Complete checkout with delivery information
- **Payment Integration** - Secure payments powered by Stripe
- **Order Tracking** - Real-time order status updates
- **Order History** - View past orders and reorder favorite items

### 👨‍💼 Admin Features
- **Food Management** - Add, edit, and delete menu items with image uploads
- **Order Management** - View and update order statuses in real-time
- **Analytics Dashboard** - Monitor sales and order metrics
- **Inventory Control** - Manage food item availability

## 🏗️ Architecture Overview

```mermaid
graph TB
    subgraph "Frontend Applications"
        C[Client App<br/>React + Vite]
        A[Admin Panel<br/>React + Vite]
    end
    
    subgraph "Backend Services"
        S[Express Server<br/>Node.js]
        DB[(MongoDB<br/>Database)]
        ST[Stripe<br/>Payment Gateway]
    end
    
    subgraph "External Services"
        IMG[Image Storage<br/>Multer]
    end
    
    C --> S
    A --> S
    S --> DB
    S --> ST
    S --> IMG
    
    style C fill:#61dafb
    style A fill:#61dafb
    style S fill:#68cc68
    style DB fill:#47a248
    style ST fill:#635bff
```

## 🚀 Tech Stack

### Frontend
- **React 18.3.1** - Modern UI library with hooks
- **React Router DOM** - Client-side routing
- **Axios** - HTTP client for API calls
- **Vite** - Fast build tool and development server
- **CSS3** - Custom styling with responsive design

### Backend
- **Node.js** - JavaScript runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database with Mongoose ODM
- **JWT** - JSON Web Tokens for authentication
- **Multer** - File upload middleware
- **bcrypt** - Password hashing
- **CORS** - Cross-origin resource sharing

### Payment & External Services
- **Stripe** - Payment processing platform
- **Dotenv** - Environment variable management

## 📊 Data Flow

```mermaid
sequenceDiagram
    participant U as User
    participant C as Client App
    participant S as Server
    participant DB as MongoDB
    participant ST as Stripe
    
    U->>C: Browse Menu
    C->>S: GET /api/food
    S->>DB: Fetch Food Items
    DB-->>S: Return Food Data
    S-->>C: JSON Response
    C-->>U: Display Menu
    
    U->>C: Add to Cart
    C->>S: POST /api/cart/add
    S->>DB: Update User Cart
    
    U->>C: Place Order
    C->>S: POST /api/order/place
    S->>ST: Create Payment Intent
    ST-->>S: Payment Confirmation
    S->>DB: Save Order
    S-->>C: Order Success
```

## 🗂️ Project Structure

```
food-delivery-app/
├── 📁 server/                  # Backend API
│   ├── 📁 config/             # Database configuration
│   ├── 📁 controllers/        # Business logic
│   ├── 📁 middleware/         # Auth & validation
│   ├── 📁 models/             # Database schemas
│   ├── 📁 routes/             # API endpoints
│   ├── 📁 uploads/            # Food images
│   ├── 📄 server.js           # Main server file
│   └── 📄 .env.example        # Environment template
├── 📁 client/                 # Customer frontend
│   ├── 📁 src/
│   │   ├── 📁 components/     # Reusable UI components
│   │   ├── 📁 pages/          # Page components
│   │   ├── 📁 context/        # Global state management
│   │   └── 📁 assets/         # Images & icons
│   └── 📄 package.json
├── 📁 admin/                  # Admin panel
│   ├── 📁 src/
│   │   ├── 📁 components/     # Admin UI components
│   │   └── 📁 pages/          # Admin pages
│   └── 📄 package.json
└── 📄 README.md
```

## 🛠️ Installation & Setup

### Prerequisites
- Node.js 18.x or higher
- npm or yarn
- MongoDB database
- Stripe account for payments

### 1. Clone the Repository
```bash
git clone <repository-url>
cd food-delivery-app
```

### 2. Environment Setup
Create `.env` file in the server directory:
```bash
cp server/.env.example server/.env
```

Configure your environment variables:
```env
JWT_SECRET=your_super_secret_jwt_key
STRIPE_SECRET_KEY=sk_test_your_stripe_secret_key
MONGODB_URI=mongodb://localhost:27017/food-delivery
PORT=4000
```

### 3. Install Dependencies

#### Server Setup
```bash
cd server
npm install
```

#### Client Setup
```bash
cd client
npm install
```

#### Admin Panel Setup
```bash
cd admin
npm install
```

### 4. Start Development Servers

#### Start Backend Server
```bash
cd server
npm run server
```

#### Start Client Application
```bash
cd client
npm run dev
```

#### Start Admin Panel
```bash
cd admin
npm run dev
```

## 🌐 API Endpoints

### Authentication
- `POST /api/user/register` - User registration
- `POST /api/user/login` - User login

### Food Management
- `GET /api/food/list` - Get all food items
- `POST /api/food/add` - Add new food item (Admin)
- `POST /api/food/remove` - Remove food item (Admin)

### Cart Operations
- `POST /api/cart/add` - Add item to cart
- `POST /api/cart/remove` - Remove item from cart
- `POST /api/cart/get` - Get cart items

### Order Management
- `POST /api/order/place` - Place new order
- `POST /api/order/verify` - Verify payment
- `POST /api/order/userorders` - Get user orders
- `GET /api/order/list` - Get all orders (Admin)
- `POST /api/order/status` - Update order status (Admin)

## 🎨 UI Components

### Customer App Components
- **Navbar** - Navigation with cart icon and user menu
- **Header** - Hero section with call-to-action
- **ExploreMenu** - Category-based food filtering
- **FoodDisplay** - Grid layout for food items
- **FoodItem** - Individual food card with add/remove functionality
- **Cart** - Shopping cart with checkout
- **LoginPopup** - Authentication modal

### Admin Panel Components
- **Sidebar** - Navigation menu for admin functions
- **Add** - Food item creation form
- **List** - Food items management table
- **Orders** - Order status management interface

## 🔐 Security Features

- **JWT Authentication** - Secure user sessions
- **Password Hashing** - bcrypt encryption
- **Input Validation** - Server-side validation
- **CORS Protection** - Cross-origin request handling
- **Environment Variables** - Sensitive data protection

## 🚀 Deployment

### Production Build
```bash
# Client build
cd client && npm run build

# Admin build
cd admin && npm run build
```

## � Acknowledgments

- React team for the amazing library
- Express.js for the robust backend framework
- MongoDB for the flexible database solution
- Stripe for seamless payment processing
- Vite for the lightning-fast build tool

---

<div align="center">
  <p>Made with ❤️ for food lovers everywhere</p>
  <p>
    <a href="#-food-delivery-app">⬆ Back to top</a>
  </p>
</div>
