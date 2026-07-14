# 🛒 ChienVHShop - E-Commerce Platform

![ASP.NET MVC](https://img.shields.io/badge/ASP.NET%20MVC-5.2.3-blue?style=flat-square)
![Entity Framework](https://img.shields.io/badge/Entity%20Framework-6.1.3-blue?style=flat-square)
![.NET Framework](https://img.shields.io/badge/.NET%20Framework-4.8-blue?style=flat-square)
![SQL Server](https://img.shields.io/badge/SQL%20Server-2012%2B-green?style=flat-square)
![License](https://img.shields.io/badge/License-Free%20Educational-green?style=flat-square)

A comprehensive, production-ready **e-commerce platform** specializing in electronics sales (iPhones, iPads, MacBooks). Built with cutting-edge ASP.NET MVC 5 and Entity Framework 6, this project demonstrates enterprise-level web development patterns, industry best practices, and real-world payment integration.

---

## 📋 Table of Contents
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation & Setup](#-installation--setup)
- [Running the Application](#-running-the-application)
- [Usage Guide](#-usage-guide)
- [Architecture](#-architecture)
- [Course Curriculum](#-course-curriculum)
- [PayPal Integration](#-paypal-integration)
- [Database Schema](#-database-schema)
- [Contributing](#-contributing)

---

## ✨ Features

### 🛍️ Customer Features
- **Product Browsing** - Browse electronics with advanced filtering by category, color, and model
- **Pagination** - Efficient product listing with PagedList pagination
- **Shopping Cart** - Session-based cart management with real-time updates
- **Checkout** - Seamless checkout experience with multiple payment options
- **PayPal Integration** - Secure payment processing via PayPal SDK
- **Order Management** - View order history and detailed order information
- **News/Blog** - Read latest product announcements and articles
- **Contact Form** - Submit inquiries with reCAPTCHA validation

### 👨‍💼 Admin Features
- **Product Management** - Full CRUD operations for products (create, read, update, delete)
- **Category Management** - Organize products into categories
- **Color & Model Variants** - Manage product attributes
- **News Management** - Publish and edit blog content
- **Order Tracking** - Monitor order status and fulfillment
- **Crystal Reports** - Generate professional order listing reports (PDF/Excel export)
- **Data Export** - Export order data to CSV/Excel formats

### 🔐 Technical Features
- **Entity Framework ORM** - Database-agnostic data access layer
- **MVC Pattern** - Clean separation of concerns (Model-View-Controller)
- **Session Management** - Stateful shopping cart implementation
- **Form Validation** - Client-side and server-side validation
- **Responsive Design** - Bootstrap 3 for mobile-friendly UI
- **URL Routing** - RESTful URL patterns
- **Authentication Ready** - Identity framework integration

---

## 🛠️ Tech Stack

| Layer | Technology | Version |
|-------|-----------|---------|
| **Frontend** | HTML5, CSS3, Bootstrap | 3.0 |
| **Client-Side Logic** | jQuery | 1.10.2 |
| **Web Framework** | ASP.NET MVC | 5.2.3 |
| **ORM** | Entity Framework | 6.1.3 |
| **Runtime** | .NET Framework | 4.8 |
| **Database** | SQL Server | 2012+ |
| **Payment Gateway** | PayPal SDK | 1.8.0 |
| **Reporting** | SAP Crystal Reports | 13.0 |
| **Pagination** | PagedList | 1.17.0 |
| **Validation** | jQuery Validate | - |
| **JSON** | Newtonsoft.Json | 10.0.3 |

---

## 📁 Project Structure

```
ChienVHShop/
├── ChienVHShop.sln                 Solution file
├── ChienVHShopOnline/              Main web project
│
├── Controllers/                     HTTP request handlers
│   ├── HomeController.cs           Landing page & home logic
│   ├── ProductsController.cs       Product listing & search
│   ├── CategoryController.cs       Category management (CRUD)
│   ├── ShoppingCartController.cs   Cart & PayPal integration ⭐
│   ├── OrderController.cs          Order history & details
│   ├── ColorsController.cs         Color attribute management
│   ├── NewsController.cs           Public news display
│   ├── NewsManagementController.cs Admin news editor
│   └── ContactUsController.cs      Contact form handler
│
├── Models/                          Data entities & business logic
│   ├── ChienVHShopModel.edmx       Entity Data Model (database schema)
│   ├── Product.cs                  Product entity with relations
│   ├── Order.cs                    Order aggregate root
│   ├── OrderDetail.cs              Order line items
│   ├── Category.cs                 Product categories
│   ├── Color.cs                    Color variants
│   ├── Model.cs                    Product model types
│   ├── User.cs                     User/seller entity
│   ├── Cart.cs                     Shopping cart model
│   ├── CaptchaResponse.cs          reCAPTCHA validation
│   ├── PaypalConfiguration.cs      PayPal SDK config
│   └── PaypalLogger.cs             PayPal logging utility
│
├── Views/                           Razor templates (UI rendering)
│   ├── Shared/
│   │   └── _MainLayout.cshtml      Master layout template
│   ├── Home/
│   │   └── Index.cshtml            Homepage
│   ├── Products/
│   │   ├── Index.cshtml            Product listing page
│   │   ├── Details.cshtml          Product detail page
│   │   └── ProductListPartial.cshtml Reusable product list component
│   ├── Category/
│   │   ├── Index.cshtml            Category list (admin)
│   │   ├── Create.cshtml           Add category form
│   │   ├── Edit.cshtml             Edit category form
│   │   ├── Details.cshtml          Category details
│   │   └── CategoryPartial.cshtml  Sidebar category widget
│   ├── ShoppingCart/               🛒 Core e-commerce views
│   │   ├── Index.cshtml            Cart display & quantity update
│   │   ├── CheckOut.cshtml         Checkout form (payment method selection)
│   │   ├── OrderSuccess.cshtml     Order confirmation (cash payment)
│   │   ├── Success.cshtml          PayPal payment success page
│   │   └── Failure.cshtml          Payment failure error page
│   ├── Order/
│   │   ├── Index.cshtml            Order list
│   │   └── Details.cshtml          Order detail with line items
│   ├── Colors/                     Color management (CRUD views)
│   ├── News/                       Public news listing
│   ├── NewsManagement/             Admin news editor (CRUD)
│   ├── ContactUs/                  Contact form
│   └── Web.config                  View engine configuration
│
├── Content/                         CSS stylesheets
│   ├── bootstrap.min.css           Bootstrap framework
│   ├── style.css                   Custom application styles
│   ├── PagedList.css               Pagination component styles
│   └── Site.css                    Additional styling
│
├── Scripts/                         JavaScript libraries & code
│   ├── jquery-1.10.2.min.js        jQuery core
│   ├── bootstrap.min.js            Bootstrap components
│   ├── jquery.validate.min.js      Form validation plugin
│   └── jquery.validate.unobtrusive.min.js ASP.NET validation
│
├── App_Start/                       Application initialization
│   ├── RouteConfig.cs              URL routing configuration
│   ├── BundleConfig.cs             CSS/JS bundling & minification
│   ├── FilterConfig.cs             Global action filters
│   ├── IdentityConfig.cs           Authentication setup
│   └── Startup.Auth.cs             OWIN startup configuration
│
├── MyReports/                       Crystal Reports
│   └── OrderListing.rpt            Professional order report template
│
├── Media/                           Static content
│   └── Images/
│       ├── Layout/                 Product images
│       └── News/                   Article images
│
├── Properties/
│   └── AssemblyInfo.cs             Assembly metadata
│
├── Web.config                       Application configuration
├── Global.asax                      Application startup
├── Default.html                     Static landing page
└── packages.config                  NuGet dependencies

```

---

## 📋 Prerequisites

### System Requirements
- **Operating System:** Windows 7 or later
- **RAM:** 4 GB minimum (8 GB recommended)
- **Disk Space:** 500 MB for installation + 1 GB for database

### Software Requirements
- **Visual Studio** 2015 or later (Community, Professional, or Enterprise)
- **.NET Framework** 4.8 (will be installed by Visual Studio)
- **SQL Server** 2012 Express or higher (can download free SQL Server Express)
- **Git** for cloning the repository
- **Internet Connection** for NuGet package restoration and PayPal sandbox access

### Recommended Tools
- **SQL Server Management Studio (SSMS)** for database management
- **Postman** for API testing (if extending with APIs)
- **Git Bash** or **GitHub Desktop** for version control

---

## 🚀 Installation & Setup

### Step 1: Clone the Repository
```bash
git clone https://github.com/Ahmed-Ragab12345/ChienVHShop.git
cd ChienVHShop
```

### Step 2: Open in Visual Studio
1. Open **Visual Studio**
2. Select **File → Open → Project/Solution**
3. Navigate to the cloned directory and select `ChienVHShop.sln`
4. Wait for Visual Studio to load the solution

### Step 3: Restore NuGet Packages
```bash
# Option 1: Via Visual Studio (Auto)
# Visual Studio will prompt to restore packages on first load

# Option 2: Via Package Manager Console
# Tools → NuGet Package Manager → Package Manager Console
# Type: Update-Package -Reinstall
```

### Step 4: Create the Database

#### Option A: Using SQL Server Management Studio (Recommended)
1. Open **SQL Server Management Studio**
2. Connect to your SQL Server instance
3. Right-click **Databases** → **New Database**
4. Name it: `ChienVHShopDB`
5. Follow the **Day 1 video** (linked below) to create tables and seed data

#### Option B: Using SQL Script
1. Create database:
```sql
CREATE DATABASE ChienVHShopDB;
USE ChienVHShopDB;
```

2. Create tables (see Database Schema section below):
```sql
CREATE TABLE Categories (
    CategoryId INT PRIMARY KEY IDENTITY(1,1),
    CategoryName NVARCHAR(100) NOT NULL
);

CREATE TABLE Products (
    ProductId INT PRIMARY KEY IDENTITY(1,1),
    ProductName NVARCHAR(100) NOT NULL,
    Price DECIMAL(10,2),
    Image NVARCHAR(255),
    CategoryId INT FOREIGN KEY REFERENCES Categories(CategoryId)
);

-- Add more tables as shown in Day 1 video
```

### Step 5: Update Connection String

1. Open `ChienVHShopOnline/Web.config`
2. Locate the `<connectionStrings>` section
3. Update the connection string to match your SQL Server:

```xml
<connectionStrings>
  <add name="ChienVHShopDBEntities" 
       connectionString="metadata=res://*/Models.ChienVHShopModel.csdl|res://*/Models.ChienVHShopModel.ssdl|res://*/Models.ChienVHShopModel.msl;provider=System.Data.SqlClient;provider connection string=&quot;Data Source=YOUR_SERVER;Initial Catalog=ChienVHShopDB;Integrated Security=true;&quot;" 
       providerName="System.Data.Entity.SqlClient" />
</connectionStrings>
```

**Replace `YOUR_SERVER` with:**
- `(LocalDb)\MSSQLLocalDB` - for LocalDB
- `.` - for local SQL Server instance
- `COMPUTER_NAME\SQLEXPRESS` - for SQL Server Express
- `server.database.windows.net` - for Azure SQL Database

### Step 6: Update Entity Framework Model (if database changed)

1. **Server Explorer** → Right-click **ChienVHShopDBEntities** → **Update Model from Database**
2. Or use **Entity Framework Power Tools** for advanced options

### Step 7: Configure PayPal (Optional)

The application includes PayPal sandbox credentials for testing. For production:

1. Sign up at [PayPal Developer](https://developer.paypal.com/)
2. Create a REST app to get your API credentials
3. Update `Web.config`:

```xml
<paypal>
  <settings>
    <add name="mode" value="sandbox"/> <!-- or "live" for production -->
    <add name="clientId" value="YOUR_PAYPAL_CLIENT_ID"/>
    <add name="clientSecret" value="YOUR_PAYPAL_CLIENT_SECRET"/>
  </settings>
</paypal>
```

---

## ▶️ Running the Application

### Method 1: Using Visual Studio (Easiest)
1. Open `ChienVHShop.sln` in Visual Studio
2. Press **F5** or click **Start** button (green play icon)
3. IIS Express will launch and open the application in your default browser
4. Navigate to `http://localhost:63801/`

### Method 2: Using IIS Express Manually
```bash
"C:\Program Files\IIS Express\iisexpress.exe" /path:C:\Path\To\ChienVHShopOnline /port:63801
```

### Method 3: Deploy to Local IIS
1. **Build Solution** (Ctrl+Shift+B)
2. Right-click `ChienVHShopOnline` project → **Publish**
3. Select **IIS** as target
4. Follow the wizard to configure the virtual directory
5. Access via `http://localhost/ChienVHShop` or custom domain

---

## 📖 Usage Guide

### For Customers

#### 🏠 Browse Products
1. Navigate to **Home** page
2. Click **Products** in the menu
3. Use **Category** sidebar to filter
4. Click product image to view details

#### 🛒 Add to Cart
1. On product details page, click **"Add to Cart"**
2. Quantity defaults to 1; adjust as needed
3. Click **"Continue Shopping"** or **"Go to Cart"**

#### 💳 Checkout & Payment
1. Click **Shopping Cart** menu
2. Review items and quantities
3. Click **"Proceed to Checkout"**
4. Choose payment method:
   - **Cash Payment** - Fill customer info, place order
   - **PayPal** - Redirect to PayPal sandbox for payment
5. Confirm order
6. View order confirmation page

#### 📧 View Orders
1. Click **My Orders** (if logged in)
2. View order history with statuses
3. Click order to see details and line items

#### 📰 Read News
1. Navigate to **News** section
2. Browse articles and announcements
3. Click article to read full content

### For Administrators

#### ➕ Manage Categories
1. Navigate to **Admin → Categories**
2. **Create:** Click "Create New" button, fill form, save
3. **Read:** View all categories in list
4. **Update:** Click category name, edit, save
5. **Delete:** Click "Delete" button, confirm

#### ➕ Manage Products
1. Navigate to **Admin → Products**
2. Similar CRUD operations as categories
3. Upload product image (stored in Media folder)
4. Assign category, color, model, storage options

#### ➕ Manage News
1. Navigate to **Admin → News Management**
2. Create articles with rich text editor
3. Upload featured images
4. Publish/unpublish articles

#### 📊 View Reports
1. Navigate to **Orders → View Report**
2. Crystal Reports generates order listing
3. Export to PDF, Excel, or print

---

## 🏗️ Architecture

### MVC Pattern Implementation

```
┌─────────────────────────────────────────────────────┐
│                    USER BROWSER                      │
│                  (HTML/CSS/jQuery)                   │
└──────────────────────┬──────────────────────────────┘
                       │ HTTP Requests/Responses
                       ▼
┌─────────────────────────────────────────────────────┐
│           VIEW LAYER (Razor Templates)               │
│  ├─ _MainLayout.cshtml (Master page)                │
│  ├─ Views/Products/Index.cshtml (Product listing)   │
│  ├─ Views/ShoppingCart/Index.cshtml (Cart display) │
│  └─ Views/Order/Details.cshtml (Order details)     │
└──────────────────────┬──────────────────────────────┘
                       │ ViewData/ViewBag
                       ▼
┌─────────────────────────────────────────────────────┐
│      CONTROLLER LAYER (Action Methods)               │
│  ├─ ProductsController.Index()                      │
│  ├─ ShoppingCartController.OrderNow(id)             │
│  ├─ ShoppingCartController.PaymentWithPaypal()      │
│  └─ OrderController.Details(id)                     │
└──────────────────────┬──────────────────────────────┘
                       │ Entity objects/IQueryable
                       ▼
┌─────────────────────────────────────────────────────┐
│       MODEL LAYER (Entity Framework)                 │
│  ├─ Product.cs, Order.cs, OrderDetail.cs           │
│  ├─ DbContext (ChienVHShopDBEntities)               │
│  └─ Relationships & Validation                      │
└──────────────────────┬──────────────────────────────┘
                       │ SQL Queries (LINQ to SQL)
                       ▼
┌─────────────────────────────────────────────────────┐
│           SQL SERVER DATABASE                        │
│  ├─ Products (id, name, price, image)              │
│  ├─ Categories, Orders, OrderDetails               │
│  └─ Users, News, Colors, Models                    │
└─────────────────────────────────────────────────────┘
```

### Data Flow: Shopping Cart Example

```
1. User clicks "Add to Cart" button
   ↓
2. Browser sends GET request to ShoppingCartController.OrderNow(productId)
   ↓
3. Controller retrieves Product from database via Entity Framework
   ↓
4. Creates Cart object: new Cart(product, quantity: 1)
   ↓
5. Stores List<Cart> in Session["Cart"] (server-side session state)
   ↓
6. View renders cart items from Session with Bootstrap table
   ↓
7. User updates quantities or removes items
   ↓
8. Form posts to ShoppingCartController.UpdateCart()
   ↓
9. Controller updates Session["Cart"] quantities
   ↓
10. User clicks "Checkout"
    ↓
11. PaymentWithPaypal() creates PayPal payment object with cart items
    ↓
12. PayPal SDK redirects to PayPal sandbox for approval
    ↓
13. PayPal redirects back with PayerID
    ↓
14. Controller executes payment and saves Order + OrderDetails to database
    ↓
15. Session["Cart"] is cleared
    ↓
16. Success page displays confirmation
```

### Session-Based Cart (Why Not Database?)
- **Advantages:** Fast performance, no database bloat, temporary state
- **Disadvantages:** Lost on session timeout, server-dependent
- **Use Case:** Suitable for single-server deployments; consider database for distributed systems

---

## 📚 Course Curriculum

### Full 22-Day Training Course on YouTube

Complete video series covering every aspect of this project:

#### **🎥 Setup & Database (Days 1-3)**
- **Day 1:** [Create Database Using SQL Server](https://www.youtube.com/watch?v=VImsLQRdqC8&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY)
  - Design database schema, create tables, relationships, seed data
- **Day 2:** [Create Web UI Using HTML & CSS](https://www.youtube.com/watch?v=fPX_vrVRE_8&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=2)
  - Bootstrap responsive design, layout structure, CSS styling
- **Day 3:** [Hosting Site on IIS & Create Layout](https://www.youtube.com/watch?v=lUYZrHSgKAY&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=3)
  - IIS configuration, virtual directories, master layout template

#### **🎥 MVC Fundamentals (Days 4-9)**
- **Day 4:** [Query Data Using MVC Model](https://www.youtube.com/watch?v=uhwAU59ZaZo&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=4)
  - Entity Framework basics, LINQ queries, ViewBag/ViewData
- **Day 5:** [Pagination in ASP.Net MVC](https://www.youtube.com/watch?v=ueBvK-HlLfY&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=5)
  - PagedList implementation, dynamic paging, routing
- **Day 6:** [Setup IIS For MVC Website](https://www.youtube.com/watch?v=Z5RQXFZInPA&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=6)
  - IIS Express, debugging, deployment preparation
- **Day 7:** [CRUD Operations - Create](https://www.youtube.com/watch?v=REpWg9eIk84&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=7)
  - Create action (GET/POST), model binding, validation
- **Day 8:** [CRUD Operations - Continue](https://www.youtube.com/watch?v=B9IJsb-NOs8&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=8)
  - Edit/Update operations, Delete functionality
- **Day 9:** [Updating Related Data](https://www.youtube.com/watch?v=yHbXt25sElI&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=9)
  - Foreign key relationships, entity associations, cascade operations

#### **🎥 E-Commerce Features (Days 10-15)**
- **Day 10:** [Shopping Cart Implementation](https://www.youtube.com/watch?v=h_jfcLICk_8&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=10)
  - Cart model, session state, add to cart functionality
- **Day 11:** [Update Cart Quantities](https://www.youtube.com/watch?v=mTJqLxkdASc&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=11)
  - Form collection binding, dynamic quantity updates, remove items
- **Day 12:** [Shopping Cart Styling](https://www.youtube.com/watch?v=v76RUAwToRY&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=12)
  - Bootstrap cart table, responsive design, UX improvements
- **Day 13:** [Product Details from Cart](https://www.youtube.com/watch?v=l_FVSNPEk68&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=13)
  - Product detail view, product specifications, related products
- **Day 14:** [Checkout & Order Processing](https://www.youtube.com/watch?v=1bhzSk5xTP4&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=14)
  - Checkout form, customer info collection, order creation
- **Day 15:** [Order & Order Details](https://www.youtube.com/watch?v=y_wbaUetQb4&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=15)
  - Order aggregates, line items, order relationships

#### **🎥 Advanced Features (Days 16-22)**
- **Day 16:** [Install Crystal Reports](https://www.youtube.com/watch?v=2Zlt4WjDbhQ&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=16)
  - Crystal Reports installation, setup, template creation
- **Day 17:** [Crystal Reports Integration](https://www.youtube.com/watch?v=UXuJx81q1Jc&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=17)
  - Report binding, export to PDF/Excel, print functionality
- **Day 18:** [Filtering & Paging](https://www.youtube.com/watch?v=WhPBiTx6vGA&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=18)
  - Advanced filtering, multi-column sorting, dynamic queries
- **Day 19:** [Google reCAPTCHA Implementation](https://www.youtube.com/watch?v=da1xNR-eajI&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=19)
  - Bot prevention, form validation, API integration
- **Day 20:** [Export to CSV/Excel](https://www.youtube.com/watch?v=Ggz9vsBRhuM&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=20)
  - EPPlus library, data export, file download handling
- **Day 21:** [PayPal Integration](https://www.youtube.com/watch?v=dQAepgwvuEk&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=21)
  - PayPal SDK setup, payment processing, redirect flow
- **Day 22:** [Project Summary & Best Practices](https://www.youtube.com/watch?v=zP6OKn_UIGc&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY&index=22)
  - Code review, optimization tips, production deployment

### 🎓 Setup Video
**Important:** Watch this setup video first for local environment configuration:
- [Setup & Installation Guide](https://www.youtube.com/watch?v=WWpauKF__fQ&list=UUMmPgIi9x7x1heJsPrf4biA)

### 📺 Complete Playlist
**Full Course:** [ASP.NET MVC & Entity Framework Training (22 Days)](https://www.youtube.com/watch?v=VImsLQRdqC8&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY)

---

## 💳 PayPal Integration

### Overview
The application uses **PayPal REST API** for secure online payments. The integration handles the complete payment flow from cart checkout to order confirmation.

### Payment Flow Architecture

```
┌────────────────────────────────────────────────────────────┐
│  Step 1: User clicks "Pay with PayPal" button on checkout  │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌────────────────────────────────────────────────────────────┐
│  Step 2: CreatePayment() builds PayPal transaction         │
│  ├─ Items: cart products with prices & quantities         │
│  ├─ Payer: payment_method = "paypal"                       │
│  ├─ Amount: total + tax + shipping                         │
│  └─ Redirect URLs: success & cancel endpoints             │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌────────────────────────────────────────────────────────────┐
│  Step 3: Payment.Create(apiContext) sends to PayPal        │
│  PayPal returns: approval_url in links                      │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌────────────────────────────────────────────────────────────┐
│  Step 4: Redirect user to PayPal sandbox for approval      │
│  User logs in & approves payment at PayPal.com             │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌────────────────────────────────────────────────────────────┐
│  Step 5: PayPal redirects back with PayerID parameter      │
│  Browser back to: /ShoppingCart/PaymentWithPaypal?         │
│                    PayerID=XXXXX&guid=XXXXX                │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌────────────────────────────────────────────────────────────┐
│  Step 6: ExecutePayment() completes transaction            │
│  ├─ Retrieve paymentId from Session[guid]                  │
│  ├─ Call Payment.Execute(apiContext, paymentExecution)    │
│  └─ PayPal confirms payment & returns state="approved"     │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌────────────────────────────────────────────────────────────┐
│  Step 7: Save Order to Database                            │
│  ├─ Create Order with customer info & paymentId            │
│  ├─ Create OrderDetails for each cart item                 │
│  └─ Clear Session["Cart"]                                  │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌────────────────────────────────────────────────────────────┐
│  Step 8: Display success page with order confirmation      │
└────────────────────────────────────────────────────────────┘
```

### Configuration

**Sandbox Mode** (Testing - Default)
```xml
<!-- Web.config -->
<paypal>
  <settings>
    <add name="mode" value="sandbox"/>
    <add name="clientId" value="AWRFwfIlAy3FwoBLtzcZSI30wn7mkXFHfXe_VK0SI_dG4zQGI0lSS98Qbb3XOXr_jqH2F_NG-6gkanYt"/>
    <add name="clientSecret" value="EBX30hduBqtkBxkbz03E2j7eczWWpLz55XP4BdrkssdgeAPhC_xUhBgZfBLLzJVGAn3KTjJIYIsu6ueC"/>
  </settings>
</paypal>
```

**Live Mode** (Production)
1. Get credentials from [PayPal Developer Dashboard](https://developer.paypal.com/)
2. Update `Web.config`:
```xml
<add name="mode" value="live"/>
<add name="clientId" value="YOUR_LIVE_CLIENT_ID"/>
<add name="clientSecret" value="YOUR_LIVE_CLIENT_SECRET"/>
```

### Key Code Components

**PayPal Configuration** (`Models/PaypalConfiguration.cs`):
```csharp
public static APIContext GetAPIContext()
{
    var apiContext = new APIContext(new OAuthTokenCredential(...));
    // Service configuration setup
    return apiContext;
}
```

**Payment Creation** (`Controllers/ShoppingCartController.cs`):
```csharp
private Payment CreatePayment(APIContext apiContext, string redirectUrl)
{
    // Build items list from shopping cart
    // Create payer and amount objects
    // Return payment.Create(apiContext)
}
```

**Payment Execution**:
```csharp
private Payment ExecutePayment(APIContext apiContext, string payerId, string paymentId)
{
    var paymentExecution = new PaymentExecution { payer_id = payerId };
    return payment.Execute(apiContext, paymentExecution);
}
```

### Testing PayPal Sandbox

1. **Buyer Account:** Use test account from [Sandbox Accounts](https://developer.paypal.com/dashboard/accounts)
2. **Test Payment:** Complete payment flow with test credentials
3. **Transaction History:** View in [Sandbox Dashboard](https://www.sandbox.paypal.com)
4. **Error Handling:** All exceptions are logged to `logs/log.txt`

---

## 🗄️ Database Schema

### ER Diagram

```
┌─────────────┐
│  USERS      │
├─────────────┤
│ UserId (PK) │
│ UserName    │
│ Email       │
└────┬────────┘
     │
     │ 1:N
     ▼
┌──────────────────────┐     ┌──────────────────┐
│  PRODUCTS            │◄────┤  CATEGORIES      │
├──────────────────────┤     ├──────────────────┤
│ ProductId (PK)       │     │ CategoryId (PK)  │
│ ProductName          │     │ CategoryName     │
│ Price                │     └──────────────────┘
│ Image                │
│ CategoryId (FK)      │     ┌──────────────────┐
│ ColorId (FK)         │◄────┤  COLORS          │
│ ModelId (FK)         │     ├──────────────────┤
│ StorageId (FK)       │     │ ColorId (PK)     │
│ SellStartDate        │     │ ColorName        │
│ SellEndDate          │     └──────────────────┘
│ IsNew                │
│ UserId (FK)          │     ┌──────────────────┐
└────┬─────────────────┘     │  MODELS          │
     │                       ├──────────────────┤
     │ 1:N                   │ ModelId (PK)     │
     ▼                       │ ModelName        │
┌─────────────────────┐      └──────────────────┘
│  ORDER_DETAILS      │
├─────────────────────┤      ┌──────────────────┐
│ OrderDetailId (PK)  │      │  STORAGE         │
│ OrderId (FK)        │      ├──────────────────┤
│ ProductId (FK)      │      │ StorageId (PK)   │
│ Quantity            │      │ StorageAmount    │
│ Price               │      └──────────────────┘
└────┬────────────────┘
     │ N:1
     ▼
┌─────────────────────┐      ┌──────────────────┐
│  ORDERS             │      │  NEWS            │
├─────────────────────┤      ├──────────────────┤
│ OrderId (PK)        │      │ NewsId (PK)      │
│ OrderDate           │      │ Title            │
│ CustomerName        │      │ Content          │
│ CustomerPhone       │      │ Image            │
│ CustomerEmail       │      │ CreatedDate      │
│ CustomerAddress     │      │ IsActive         │
│ PaymentType         │      └──────────────────┘
│ Status              │
│ PaymentId (Optional)│      ┌──────────────────┐
│ TransactionId       │      │  CONTACT_US      │
└─────────────────────┘      ├──────────────────┤
                             │ ContactId (PK)   │
                             │ Name             │
                             │ Email            │
                             │ Subject          │
                             │ Message          │
                             │ CreatedDate      │
                             └──────────────────┘
```

### Main Tables

| Table | Purpose | Key Fields |
|-------|---------|-----------|
| **Products** | Product catalog | ProductId, ProductName, Price, Image, CategoryId |
| **Categories** | Product grouping | CategoryId, CategoryName |
| **Orders** | Customer orders | OrderId, OrderDate, CustomerName, Status |
| **OrderDetails** | Order line items | OrderDetailId, OrderId, ProductId, Quantity |
| **Users** | Sellers/Admins | UserId, UserName, Email |
| **News** | Blog articles | NewsId, Title, Content, CreatedDate |
| **Colors** | Product colors | ColorId, ColorName |
| **Models** | Product models | ModelId, ModelName |

---

## 🤝 Contributing

Contributions are welcome! This is a learning project, so improvements, bug fixes, and enhancements are encouraged.

### How to Contribute

1. **Fork the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/ChienVHShop.git
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make your changes** and test thoroughly

4. **Commit with descriptive messages**
   ```bash
   git commit -m "Add feature: description of changes"
   ```

5. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

6. **Create a Pull Request** with detailed description

### Development Guidelines
- Follow C# naming conventions (PascalCase for classes/methods)
- Add comments to complex business logic
- Test both happy path and error scenarios
- Update README if adding new features
- Keep commits atomic and focused

### Bug Reports
Found an issue? Create a GitHub issue with:
- Clear description of the bug
- Steps to reproduce
- Expected vs. actual behavior
- Environment details (OS, Visual Studio version, etc.)

---

## 📞 Support & Questions

### Resources
- **YouTube Course:** [Full 22-Day Training Series](https://www.youtube.com/watch?v=VImsLQRdqC8&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY)
- **Setup Guide:** [Installation Video](https://www.youtube.com/watch?v=WWpauKF__fQ&list=UUMmPgIi9x7x1heJsPrf4biA)
- **PayPal Docs:** [PayPal REST API Documentation](https://developer.paypal.com/docs/api/overview/)
- **ASP.NET MVC:** [Microsoft Documentation](https://docs.microsoft.com/en-us/aspnet/mvc/)
- **Entity Framework:** [EF 6 Documentation](https://docs.microsoft.com/en-us/ef/ef6/)

### FAQ

**Q: How do I change the database connection?**
A: Update the connection string in `Web.config` under `<connectionStrings>` section.

**Q: Can I use this project for production?**
A: This is a learning project. For production, consider adding authentication, HTTPS, input validation, and security hardening.

**Q: How do I integrate real PayPal payments?**
A: Switch from "sandbox" to "live" mode in `Web.config` and use production API credentials.

**Q: Can I use SQL Server instead of LocalDB?**
A: Yes, just update the connection string to point to your SQL Server instance.

**Q: How do I deploy to Azure or AWS?**
A: See deployment guides in Day 3 video, or refer to cloud provider's ASP.NET hosting documentation.

---

## 📄 License

This project is provided as **free educational material**. You are free to:
- ✅ Use for learning purposes
- ✅ Modify and extend
- ✅ Deploy for personal/educational use
- ✅ Share with others (with attribution)

---

## 🙏 Acknowledgments

- **Instructor:** [@Ahmed-Ragab12345](https://github.com/Ahmed-Ragab12345)
- **Technologies:** Microsoft, PayPal, SAP
- **Community:** All contributors and learners improving this project

---

## ⭐ Show Your Support

If this project helped you learn ASP.NET MVC and Entity Framework, please:
- ⭐ Star this repository
- 👁️ Watch for updates
- 🔗 Share with others learning web development
- 💬 Contribute improvements

**Happy Coding! 🚀**

---

<div align="center">

**Built with ❤️ for learning ASP.NET MVC development**

[GitHub](https://github.com/Ahmed-Ragab12345) • [YouTube Course](https://www.youtube.com/watch?v=VImsLQRdqC8&list=PLp1Emx1rT4z9MYuP7U8GVUMvKYz_NM9AY)

</div>
