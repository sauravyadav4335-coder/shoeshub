# 👟 ShoesHub - Premium Shoes eCommerce Application

A production-level full-stack eCommerce platform for premium shoes with a modern UI inspired by Nike and Adidas. Built with React (Vite), Node.js/Express, and MongoDB.

## 🎯 Features

### Frontend
- **Modern Premium UI** - Clean, professional design inspired by Nike/Adidas
- **Responsive Design** - Fully mobile and desktop responsive (no framework, pure CSS)
- **Product Catalog** - Browse and filter shoes by category, brand, and price
- **Shopping Cart** - Fully functional with local storage persistence
- **Authentication** - Secure signup and login with JWT
- **Checkout** - Complete order form with validation
- **Order Tracking** - View order history
- **Smooth Animations** - Page transitions, hover effects, and interactive elements
- **Toast Notifications** - User feedback messages
- **Image Gallery** - Product images with zoom effect

### Backend
- **RESTful API** - Complete REST API with proper error handling
- **Authentication** - JWT-based authentication with bcrypt password hashing
- **Database** - MongoDB with Mongoose ODM
- **Product Management** - Filter, sort, and search functionality
- **Order Processing** - Create and track orders
- **CORS** - Enabled for frontend-backend communication
- **Demo Database** - Pre-seeded with 15+ premium shoe products

## 📋 Tech Stack

### Frontend
- React 18 with Vite
- React Router DOM
- Axios for API calls
- Context API for state management
- Pure CSS (modular, responsive)

### Backend
- Node.js + Express
- MongoDB + Mongoose
- JWT (jwt-simple)
- bcryptjs for password hashing
- CORS middleware

## 🚀 Quick Start

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or Atlas cloud)
- npm or yarn

### Backend Setup

1. **Navigate to backend directory:**
   ```bash
   cd backend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure environment variables:**
   - Open `.env` file and update:
   ```env
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/shoes-ecommerce
   JWT_SECRET=your_jwt_secret_key_change_in_production
   NODE_ENV=development
   ```

4. **Start MongoDB** (if running locally):
   ```bash
   mongod
   ```

5. **Seed the database with products:**
   ```bash
   npm run seed
   ```

6. **Start the server:**
   ```bash
   npm run dev
   ```
   Server will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to frontend directory:**
   ```bash
   cd frontend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the development server:**
   ```bash
   npm run dev
   ```
   Frontend will run on `http://localhost:5173`

## 📱 Pages & Features

### Home Page
- Auto-sliding hero carousel with CTA button
- Product categories section
- Featured products grid
- Special offers banner
- Features showcase (shipping, returns, security)

### Shop Page
- Grid layout with 15+ products
- Filters:
  - Price range
  - Category
  - Brand
  - Sorting (low-to-high, high-to-low)
- Responsive mobile-friendly layout
- Product count display

### Product Details Page
- Image gallery with thumbnail previews
- Zoom effect on hover
- Product information (price, rating, description)
- Size selection
- Quantity selector
- Add to cart with animation
- Product specifications
- Feature badges (authentic, free shipping, easy returns)

### Cart Page
- Display all cart items
- Edit quantity or remove items
- Order summary with subtotal, shipping, and tax
- Checkout button
- Clear cart option

### Checkout Page
- Comprehensive form validation
- Shipping address input
- Payment information form
- Order summary sidebar
- Order confirmation

### Authentication
- Signup page with validation
- Login page with credentials check
- Error handling

### Orders Page
- View all user orders
- Order status badges
- Order items and total price
- Shipping address details

### Navigation
- Sticky navbar with smooth transitions
- Cart icon with item count badge
- User dropdown menu
- Mobile hamburger menu
- Footer with links and social icons

## 🔐 Authentication & Security

- **JWT Authentication** - Secure token-based authentication
- **Password Hashing** - bcryptjs for secure password storage
- **Protected Routes** - Checkout and orders require authentication
- **Token Persistence** - Tokens saved in localStorage
- **Error Handling** - Proper error messages for failed operations

## 🗄️ Database Schema

### Product
```javascript
{
  name: String,
  brand: String,
  category: String,
  price: Number,
  description: String,
  images: [String],
  sizes: [Number],
  stock: Number,
  rating: Number,
  reviews: Number
}
```

### User
```javascript
{
  name: String,
  email: String (unique),
  password: String (hashed),
  role: String (user/admin)
}
```

### Order
```javascript
{
  user: ObjectId,
  items: [{productId, name, price, quantity, size, image}],
  totalPrice: Number,
  address: {street, city, state, postalCode, country},
  status: String,
  paymentMethod: String
}
```

## 🎨 UI/UX Highlights

- **Professional Design** - Nike/Adidas inspired minimalist aesthetic
- **Smooth Animations** - CSS transitions and keyframe animations
- **Responsive Grid** - CSS Grid and Flexbox layouts
- **Color Scheme** - Black, white, orange accent colors
- **Typography** - Clean, modern font stack
- **Shadows & Depth** - Multi-level box shadows for depth
- **Hover Effects** - Interactive feedback on buttons and cards
- **Loading States** - Skeleton loaders and spinners
- **Toast Notifications** - Non-intrusive user feedback

## 📱 Responsive Breakpoints

- **Desktop** - Above 1024px
- **Tablet** - 768px to 1024px
- **Mobile** - Below 768px
- **Small Mobile** - Below 480px

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/register` - Create new account
- `POST /api/auth/login` - Login user

### Products
- `GET /api/products` - Get all products with filters
- `GET /api/products/:id` - Get single product

### Orders
- `POST /api/orders` - Create new order (protected)
- `GET /api/orders` - Get user's orders (protected)

## 🌳 Project Structure

```
ROOT/
├── backend/
│   ├── models/
│   │   ├── Product.js
│   │   ├── User.js
│   │   └── Order.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── productController.js
│   │   └── orderController.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── products.js
│   │   └── orders.js
│   ├── middleware/
│   │   └── auth.js
│   ├── config/
│   │   └── db.js
│   ├── seeds/
│   │   └── seedProducts.js
│   ├── server.js
│   ├── package.json
│   └── .env
│
└── frontend/
    ├── src/
    │   ├── components/
    │   │   ├── Navbar.js
    │   │   ├── Footer.js
    │   │   ├── ProductCard.js
    │   │   ├── Toast.js
    │   │   └── Loader.js
    │   ├── pages/
    │   │   ├── Home.js
    │   │   ├── Shop.js
    │   │   ├── ProductDetails.js
    │   │   ├── Cart.js
    │   │   ├── Checkout.js
    │   │   ├── Login.js
    │   │   ├── Signup.js
    │   │   └── Orders.js
    │   ├── context/
    │   │   ├── AuthContext.js
    │   │   └── CartContext.js
    │   ├── services/
    │   │   └── api.js
    │   ├── styles/
    │   │   ├── global.css
    │   │   ├── Navbar.css
    │   │   ├── Footer.css
    │   │   ├── ProductCard.css
    │   │   ├── Toast.css
    │   │   ├── Loader.css
    │   │   ├── Home.css
    │   │   ├── Shop.css
    │   │   ├── ProductDetails.css
    │   │   ├── Cart.css
    │   │   ├── Checkout.css
    │   │   ├── Auth.css
    │   │   └── Orders.css
    │   ├── App.js
    │   └── main.js
    ├── index.html
    ├── vite.config.js
    ├── tsconfig.json
    ├── package.json
    └── .gitignore
```

## 🧪 Testing the Application

### Test Workflow
1. Visit `http://localhost:5173`
2. Browse products on Home and Shop pages
3. Click a product to see details
4. Add items to cart
5. Proceed to checkout
6. Sign up or login with your account
7. Complete checkout form
8. View your orders

## 🚄 Performance Optimizations

- **Lazy Loading** - Images load on demand
- **Local Storage** - Cart persists across sessions
- **CSS Optimization** - Modular CSS with no unused styles
- **Code Splitting** - React Router handles route splitting
- **Smooth Transitions** - Hardware-accelerated CSS animations

## 🔧 Configuration

### Ports
- Backend API: `5000`
- Frontend Dev Server: `5173`

### Environment Variables

**Backend (.env)**
```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/shoes-ecommerce
JWT_SECRET=your_secret_key
NODE_ENV=development
```

## 📝 Notes

- The payment form is UI-only (no actual payment processing)
- Demo database includes 15 premium shoe products
- All prices are in USD
- Cart data persists in localStorage
- Authentication tokens expire based on JWT settings

## 🤝 Contributing

Feel free to extend this project with:
- Real payment integration (Stripe, PayPal)
- Admin dashboard
- Product reviews and ratings
- Wishlist functionality
- Email notifications
- Advanced analytics
- API documentation with Swagger

## 📄 License

This project is created for educational purposes.

## 🎓 Learning Resources

Built with:
- React documentation: https://react.dev
- Express documentation: https://expressjs.com
- MongoDB documentation: https://docs.mongodb.com
- CSS modern features: https://developer.mozilla.org/en-US/docs/Web/CSS

---

**Enjoy building with ShoesHub! 👟**
