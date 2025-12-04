

Restaurant Food Ordering Management System (MERN)
A simple full-stack application where users browse restaurants, view menus, place orders, and track order status. Admins/owners manage their restaurant, menus, and orders.

1. Problem Statement
Students must build a basic restaurant food-ordering system with:
User-side flow for browsing restaurants → selecting dishes → placing orders

Owner/Admin-side flow for managing restaurant details, menus, and order statuses

Persistent data storage

Simple UI for navigation

Basic authentication 

 2. Tech Stack
Frontend: React, Axios, Tailwind 
Backend: Node.js, Express.js
Database: MongoDB
Other: Multer/Cloudinary , JWT/Auth0 , Stripe 

3. Project Workflow (Core Explanation)
A. User Workflow
Home Page Loads
Frontend requests list of restaurants from backend
: GET /api/restaurants

User Selects a Restaurant

Menu items fetched

API: GET /api/restaurants/:id

User Adds Items to Cart

Cart stored in frontend state/localStorage

User Places Order

Cart + user details sent to backend

API: POST /api/orders

Backend creates order entry in DB → returns order confirmation

User Checks Order Status

API: GET /api/orders/:id

Status updates in real-time when restaurant changes it

B. Restaurant Owner Workflow

Owner Logs In

Token generated 

Owner Creates/Updates Restaurant

API: POST /api/my/restaurant or PUT /api/my/restaurant

Owner Adds Menu Items


API: POST /api/my/restaurant/menu

Owner Views Orders

API: GET /api/my/restaurant/orders

Owner Updates Order Status

API: PATCH /api/my/restaurant/orders/:id
Status options typically:
placed → confirmed → preparing → out_for_delivery → completed


project/
├── backend/
│   ├── src/
│   │   ├── models/         # MongoDB schemas
│   │   ├── routes/         # API endpoints
│   │   ├── controllers/    # Business logic
│   │   ├── middleware/     # Auth, error handling
│   │   └── index.js        # Server entry
│   └── package.json
│
├── frontend/
│   ├── src/
│   │   ├── components/     # UI elements
│   │   ├── pages/          # Screens
│   │   ├── api/            # Axios API calls
│   │   └── App.jsx
│   └── package.json
│
└── README.md



▶5. Project Setup Steps
Backend
cd backend
npm install
npm run dev

Frontend
cd frontend
npm install
npm run dev

Backend default: http://localhost:7001
Frontend default: http://localhost:5173


Frontend
VITE_API_BASE_URL="http://localhost:7001"


 Database Schema (Simple & Clean)
Restaurant
{
  "name": "String",
  "city": "String",
  "cuisine": ["String"],
  "menu": ["MenuItem"]
}

MenuItem
{
  "name": "String",
  "price": "Number",
  "image": "String"
}

Order
{
  "items": ["MenuItem"],
  "restaurantId": "ObjectId",
  "status": "String",
  "totalAmount": "Number"
}

9. API Documentation 
Restaurant APIs
GET /api/restaurants
GET /api/restaurants/:id
POST /api/my/restaurant
PUT /api/my/restaurant

Order APIs
POST /api/orders
GET /api/orders/:id
PATCH /api/my/restaurant/orders/:id


