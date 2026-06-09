# LumaStore 🛒

[![Live Demo](https://img.shields.io/badge/Live-Demo-brightgreen.svg)](https://ecom-orcin-theta.vercel.app/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-blue.svg)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-success.svg)](https://www.mongodb.com/)

LumaStore is a full-stack, responsive e-commerce platform engineered with a robust Node.js and Express backend. It features comprehensive Role-Based Access Control (RBAC), secure authentication, and a dynamic inventory management system designed for both everyday users and store administrators.

## 🚀 Live Application
**Experience the live application here:** [LumaStore on Vercel](https://ecom-orcin-theta.vercel.app/)

## ✨ Key Features
* **Role-Based Access Control (RBAC):** Distinct routing and middleware flows isolating standard users from owner/admin privileges.
* **Secure Authentication:** End-to-end security using `bcrypt` for password hashing and JSON Web Tokens (JWT) for stateless, cookie-based session management.
* **Dynamic Cart & Order Management:** Complex Mongoose relational data modeling linking User, Product, and Order schemas via document ObjectIds.
* **Memory-Based Media Handling:** Secure, direct binary image uploads to the database utilizing `multer` memory storage.
* **Serverless Optimization:** Custom backend configuration specifically optimized for instantaneous deployment on Vercel's Edge network.

## 🛠️ Technical Stack
* **Frontend:** EJS (Embedded JavaScript templates), Tailwind CSS, HTML5
* **Backend:** Node.js, Express.js
* **Database:** MongoDB Atlas, Mongoose
* **Authentication:** JWT, bcrypt
* **Deployment:** Vercel (Serverless), GitHub

## 🧠 Technical Challenges & Solutions

Building a traditional Express application and adapting it for modern serverless deployment presented several architectural challenges:

**1. Vercel Serverless Routing for EJS Templates**
* **Challenge:** Transitioning a monolithic Express app to Vercel's serverless architecture resulted in failed view lookups, as serverless environments do not bundle static assets by default.
* **Solution:** Engineered a custom `vercel.json` build configuration using the `@vercel/node` runtime to explicitly bundle static `views` and `public` directories, routing all dynamic endpoints seamlessly through serverless functional handlers.

**2. Handling Ephemeral File Systems for Image Uploads**
* **Challenge:** Traditional disk-storage image uploads fail on serverless platforms (like Vercel) due to their stateless, ephemeral file systems.
* **Solution:** Configured `multer` to utilize `memoryStorage()`. This processes incoming image streams as binary buffers in memory, allowing the system to pass image data directly to MongoDB without ever relying on the local server disk.

**3. Dynamic Tailwind CSS Integration**
* **Challenge:** Maintaining consistent utility-class styling and responsive design across dynamic, server-rendered EJS partials.
* **Solution:** Standardized UI components across the views directory, ensuring predictable rendering and a clean user experience for both the consumer storefront and the administrative dashboards.

## 💻 Local Installation & Setup

To run LumaStore locally, follow these steps:

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/LumaStore.git](https://github.com/your-username/LumaStore.git)
   cd LumaStore


2. **Install dependencies:**

```Bash
npm install
```


3. **Configure Environment Variables:**
Create a `.env` file in the root directory and add the following keys:

```
Code snippet

PORT=3000
MONGODB_URL=your_mongodb_atlas_connection_string
JWT_SECRET=your_secure_jwt_secret
NODE_ENV=development
```


4. **Start the server:**

```Bash
npx nodemon app.js
```

The application will be running at http://localhost:3000

Designed and Developed by Subhajit Das
