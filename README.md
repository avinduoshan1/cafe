Café Elixir - Point of Sale Management System
Project Overview
Café Elixir is a comprehensive Java desktop application designed for café and restaurant management. Built with Java Swing and MySQL, it provides a complete solution for managing products, processing orders, handling payments, and tracking sales.

🎯 Key Features

User Authentication & Security
Secure Login System: Password-protected access with username validation
Sign Up Functionality: New admin registration with security questions
Password Recovery: Forgot password feature using security question verification
Password Visibility Toggle: Show/hide password for better user experience
Product Management
Add Products: Upload product images, set names and prices
View All Products: Display products in a table with images
Update Products: Modify product details (name, price)
Delete Products: Remove products from inventory
Image Handling: Store and display product images using BLOB storage
Order Processing
Product Selection: Browse available products with visual display
Cart Management: Add products to cart with quantity selection
Real-time Total Calculation: Automatic price calculation based on quantity
Order Summary: View cart items before payment
Payment & Billing
Tax Calculation: Automatic tax computation based on subtotal
Dynamic Tax Tiers:
Rs. 10-20: 0.5 tax
Rs. 20-30: 1.0 tax
Rs. 30-40: 1.5 tax
Rs. 40-60: 2.0 tax
Rs. 60-80: 3.0 tax
Rs. 80-100: 4.0 tax
Rs. 100-150: 8.0 tax
Rs. 150-200: 8.0 tax
Rs. 200+: 10.0 tax
Change Calculation: Automatic change computation
Customer Details: Record customer name with each transaction
Receipt Printing: Print receipts with order details
Payment Date Tracking: Automatic date recording
Order History
View All Orders: Complete history of all transactions
Order Details: Payment ID, customer name, product IDs, product names, total price, and payment date
Sales Tracking: Monitor all completed transactions
User Interface
Modern GUI: Custom-designed interface with Swing components
Draggable Windows: Move windows by clicking and dragging
Smooth Animations: Fade-in effects for window opening
Responsive Tables: Scrollable tables with custom cell renderers
Image Display: Product images rendered in table cells (100x100px)
🛠️ Technologies Used
Frontend
Java Swing: GUI framework for desktop interface
AWT: Abstract Window Toolkit for event handling
Custom Components: Custom table cell renderers for images
Backend
Java: Core programming language (Java 23)
JDBC: Database connectivity
MySQL Connector: Version 9.3.0
Database
MySQL: Relational database management
Tables:
admin: User authentication data
product: Product catalog with BLOB images
cart: Shopping cart items
payment: Transaction records
Build Tools
Apache Ant: Build automation
NetBeans: IDE project structure
📊 Database Schema
Admin Table
id (INT): Primary key
username (VARCHAR): Admin username
password (VARCHAR): Encrypted password
s_ques (VARCHAR): Security question
ans (VARCHAR): Security answer
Product Table
id (INT): Primary key, auto-increment
name (VARCHAR): Product name
price (DOUBLE): Product price
image (BLOB): Product image data
Cart Table
cid (INT): Cart ID
pid (INT): Product ID
pName (VARCHAR): Product name
qty (INT): Quantity
price (DOUBLE): Unit price
total (DOUBLE): Total price (qty × price)
Payment Table
pid (INT): Payment ID
cName (VARCHAR): Customer name
proid (VARCHAR): Product IDs (comma-separated)
pName (VARCHAR): Product names (comma-separated)
total (DOUBLE): Total amount
pdate (VARCHAR): Payment date
🎨 Design Patterns Used
DAO Pattern (Data Access Object)
AdminDao.java: Admin data operations
Dao.java: Product, cart, and payment operations
Model-View-Controller (MVC)

Models: Admin.java, Product.java, cart.java, Payment.java
Views: All Frame classes (LoginFrame, HomeFrame, etc.)
Controllers: DAO classes
Singleton Pattern

MyConnection.java: Single database connection instance
Strategy Pattern

Calculate.java: Tax calculation logic
🔐 Security Features
Password masking with show/hide toggle
Security question-based password recovery
Username validation (no numbers allowed)
Duplicate username prevention
SQL injection protection using PreparedStatements
📱 User Flows
Authentication Flow
Launch Application → Login Screen
Enter credentials or Sign Up
Forgot Password option available
Security question verification
Access Home Dashboard
Product Management Flow
Home → Add Product
Upload image, enter details
Save to database
View in All Products
Manage Products (Update/Delete)
Order Processing Flow
Home → Order
Browse products with images
Select product and quantity
Add to cart
View cart summary
Enter customer details
Process payment
Print receipt
📈 Technical Highlights
Image Handling: BLOB storage and custom ImageIcon rendering
Real-time Calculations: Dynamic tax and total computation
Table Customization: Custom cell renderers for image display
Event Handling: Mouse events for drag functionality
Window Management: Undecorated frames with custom controls
Animation: Smooth fade-in effects using opacity
🎯 Key Accomplishments
✅ Complete CRUD operations for products ✅ Secure authentication system ✅ Real-time cart management ✅ Automated tax calculation ✅ Receipt printing functionality ✅ Image storage and display ✅ Transaction history tracking ✅ Custom UI components ✅ Drag-and-drop window movement ✅ Password recovery system

💡 Potential Enhancements
Multi-user role management
Inventory tracking
Sales reports and analytics
Barcode scanning integration
Email receipt delivery
Database backup/restore
Multi-language support
Theme customization
🚀 Setup Instructions
Database Setup:

CREATE DATABASE cafe;
USE cafe;
-- Create tables as per schema
MySQL Configuration:

Default: localhost:3306
Username: root
Password: (empty)
Dependencies:

Java 23 or higher
MySQL Server
MySQL Connector/J 9.3.0
Run Application:

Open project in NetBeans
Build project (F11)
Run LoginFrame (F6)
📸 Screenshots
Key Features Demonstrated:
Login interface with password masking
Home dashboard with navigation
Product management with image upload
Order processing with cart
Payment screen with tax calculation
Order history table
🏆 Skills Demonstrated
Java Programming: Advanced OOP concepts
GUI Development: Swing framework expertise
Database Design: Relational database schema
JDBC: Database connectivity and operations
Event-Driven Programming: User interaction handling
Image Processing: BLOB storage and rendering
Software Architecture: MVC and DAO patterns
Security: Authentication and data protection
User Experience: Intuitive interface design
📝 Code Quality
Clean code structure
Separation of concerns
Reusable components
Exception handling
PreparedStatement usage for security
Proper resource management
Project Type: Desktop Application Domain: Restaurant/Café Management Complexity: Intermediate to Advanced Development Time: ~40-60 hours Lines of Code: ~4,000+

This project showcases practical application of Java desktop development skills, database integration, and user interface design for real-world business scenarios.
