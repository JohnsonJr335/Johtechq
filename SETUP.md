# 🛍️ Johtechq Shop Management System - Setup Guide

## Prerequisites

- **Node.js** (v14 or higher) - Download from [nodejs.org](https://nodejs.org)
- **MongoDB** (Local or Cloud) - [MongoDB Community Edition](https://www.mongodb.com/try/download/community)
- **npm** (comes with Node.js)

## Installation Steps

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/JohnsonJr335/Johtechq.git
cd Johtechq
```

### 2️⃣ Install All Dependencies

```bash
npm run install-all
```

This will install dependencies for:
- Root project
- Backend server
- React client
- Electron desktop app

### 3️⃣ Set Up Environment Variables

Create a `.env` file in the `server` directory:

```bash
cp server/.env.example server/.env
```

Edit `server/.env`:

```
MONGODB_URI=mongodb://localhost:27017/johtechq-shop
PORT=5000
NODE_ENV=development
```

**For MongoDB Cloud (Atlas):**
```
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/johtechq-shop
PORT=5000
NODE_ENV=development
```

### 4️⃣ Start MongoDB

**Local MongoDB:**
```bash
mongod
```

**or use MongoDB Atlas** (Cloud option)

### 5️⃣ Run the Application

**Option A: Web Application**

Terminal 1 - Start Backend:
```bash
npm run dev
```

Terminal 2 - Start React Frontend:
```bash
npm run client
```

Access at: **http://localhost:3000**

---

**Option B: Desktop Application**

Terminal 1 - Start Backend:
```bash
npm run dev
```

Terminal 2 - Start Electron App:
```bash
npm run desktop
```

---

## 🎯 Features

### Shop Management
- ✅ Product Inventory Management
  - Add/Edit/Delete Products
  - Track SKU, Cost Price, Selling Price
  - Real-time Stock Tracking
  - Low Stock Alerts

- ✅ Sales Management
  - Record Sales Transactions
  - Automatic Stock Reduction
  - Profit Calculation
  - Sales Reports

- ✅ Dashboard
  - Total Revenue
  - Total Profit
  - Average Profit Margin
  - Low Stock Alerts
  - Sales Statistics

### Digital Clock
- ✅ Multiple Timezone Display
- ✅ 600+ Timezones Supported
- ✅ Real-time Updates
- ✅ Add/Remove Zones Dynamically
- ✅ Beautiful UI with Emojis

## 📊 API Documentation

### Products Endpoints

```
GET /api/products                    - Get all products
GET /api/products/:id                - Get single product
POST /api/products                   - Create product
PUT /api/products/:id                - Update product
DELETE /api/products/:id             - Delete product
GET /api/products/stock/low          - Get low stock products
```

### Sales Endpoints

```
GET /api/sales                       - Get all sales
POST /api/sales                      - Record a sale
GET /api/sales/report/summary        - Get sales report
```

### Clock Endpoints

```
GET /api/clock                       - Get time in default zones
GET /api/clock/:timezone             - Get time in specific zone
GET /api/clock/list/all              - List all timezones
```

## 🗄️ Database Schema

### Product Model
```javascript
{
  name: String,
  description: String,
  sku: String (unique),
  costPrice: Number,
  sellingPrice: Number,
  quantity: Number,
  minStockLevel: Number,
  category: String,
  isActive: Boolean,
  createdAt: Date,
  updatedAt: Date
}
```

### Sale Model
```javascript
{
  productId: ObjectId,
  productName: String,
  quantity: Number,
  costPrice: Number,
  sellingPrice: Number,
  totalCost: Number,
  totalRevenue: Number,
  profit: Number,
  profitMargin: Number,
  saleDate: Date,
  notes: String,
  createdAt: Date,
  updatedAt: Date
}
```

## 🐛 Troubleshooting

### MongoDB Connection Failed
- Ensure MongoDB is running
- Check connection string in `.env`
- For Atlas, whitelist your IP

### Port Already in Use
```bash
# Kill process on port 5000 (or your PORT)
lsof -ti:5000 | xargs kill -9  # macOS/Linux
netstat -ano | findstr :5000    # Windows
```

### Electron Not Starting
- Make sure backend is running first
- Clear Electron cache: `rm -rf ~/.config/Electron`
- Try: `npm cache clean --force`

### React App Not Loading
- Clear browser cache (Ctrl+Shift+Delete)
- Check if port 3000 is in use
- Restart development server

## 📦 Build for Production

### Web App
```bash
cd client
npm run build
```

### Desktop App
```bash
npm run build
```

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first.

## 📝 License

MIT License - Free for personal and commercial use.

## 👤 Author

**JohnsonJr335**

---

**Happy Selling! 🛍️** ⏰

For more help, visit the GitHub repository or check the code comments.
