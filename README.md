# Café Elixir - Point of Sale System

A Java-based Point of Sale (POS) system designed for café management with a modern GUI interface built using Java Swing.

## Features

### Authentication & User Management
- Secure login system with username/password authentication
- User registration with security questions for password recovery
- Password reset functionality using security questions
- Show/hide password visibility toggle

### Product Management
- Add new products with name, price, and images
- View all products in a table with image display
- Update existing product information
- Delete products from inventory
- Browse and upload product images

### Order Management
- Create new orders by selecting products
- Add products to cart with customizable quantities
- View cart with product details and totals
- Automatic cart ID generation
- Real-time total calculation

### Payment Processing
- Complete checkout with customer information
- Automatic payment ID generation
- Tax calculation based on subtotal
- Cash payment with change calculation
- Print receipt functionality
- Payment date tracking

### Order History
- View all completed orders
- Track customer purchases
- View product details for each order
- Payment history with dates

## Technology Stack

- **Language**: Java
- **GUI Framework**: Java Swing
- **Database**: MySQL
- **JDBC Driver**: MySQL Connector/J 9.3.0
- **Build Tool**: Apache Ant (NetBeans project)
- **IDE**: NetBeans 25

## Database Schema

### Tables

#### `admin`
- `id` (INT) - Primary key
- `username` (VARCHAR) - Admin username
- `password` (VARCHAR) - Admin password
- `s_ques` (VARCHAR) - Security question
- `ans` (VARCHAR) - Security answer

#### `product`
- `id` (INT) - Primary key (auto-increment)
- `name` (VARCHAR) - Product name
- `price` (DOUBLE) - Product price
- `image` (BLOB) - Product image

#### `cart`
- `cid` (INT) - Cart ID
- `pid` (INT) - Product ID
- `pName` (VARCHAR) - Product name
- `qty` (INT) - Quantity
- `price` (DOUBLE) - Unit price
- `total` (DOUBLE) - Total price (qty × price)

#### `payment`
- `pid` (INT) - Payment ID
- `cName` (VARCHAR) - Customer name
- `proid` (VARCHAR) - Product IDs (comma-separated)
- `pName` (VARCHAR) - Product names (comma-separated)
- `total` (DOUBLE) - Total amount
- `pdate` (VARCHAR) - Payment date

## Setup Instructions

### Prerequisites
- Java Development Kit (JDK) 23 or higher
- MySQL Server
- NetBeans IDE (recommended) or any Java IDE
- MySQL Connector/J 9.3.0

### Database Setup

1. Create a MySQL database named `cafe`:
```sql
CREATE DATABASE cafe;
USE cafe;
```

2. Create the required tables:

```sql
CREATE TABLE admin (
    id INT PRIMARY KEY,
    username VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(100) NOT NULL,
    s_ques VARCHAR(255),
    ans VARCHAR(255)
);

CREATE TABLE product (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    price DOUBLE NOT NULL,
    image LONGBLOB
);

CREATE TABLE cart (
    cid INT,
    pid INT,
    pName VARCHAR(100),
    qty INT,
    price DOUBLE,
    total DOUBLE
);

CREATE TABLE payment (
    pid INT PRIMARY KEY,
    cName VARCHAR(100),
    proid VARCHAR(255),
    pName VARCHAR(255),
    total DOUBLE,
    pdate VARCHAR(50)
);
```

3. Update database connection details in `src/model/MyConnection.java`:
```java
public static final String username = "root";
public static final String password = "your_password";
public static final String url = "jdbc:mysql://localhost:3306/cafe";
```

### Application Setup

1. Clone or download the project
2. Open the project in NetBeans IDE
3. Add MySQL Connector/J library to the project:
   - Right-click on Libraries > Add JAR/Folder
   - Navigate to `mysql-connector-j-9.3.0.jar`
4. Build the project (Clean and Build)
5. Run the application

## Usage

### First Time Setup
1. Launch the application
2. Click on "SignUp" to create an admin account
3. Fill in all required information including security question
4. Login with your credentials

### Managing Products
1. From the home screen, click "Add Product"
2. Enter product name, price, and browse for an image
3. Click "Save" to add the product
4. Use "Manage Product" to update or delete existing products
5. View all products using "All Product"

### Processing Orders
1. Click "Order" from the home screen
2. Select a product from the table
3. Enter the desired quantity
4. Click "Add to Cart"
5. Click "Cart" to proceed to checkout
6. Enter customer information
7. Enter cash amount received
8. Change amount is calculated automatically
9. Click "Payment" to complete the transaction
10. Choose to print receipt (optional)

### Viewing Orders
1. Click "View Orders" from the home screen
2. View complete order history with customer details

## Project Structure

```
cafeelixir/
├── src/
│   ├── cafeelixir/
│   │   ├── AddProductFrame.java
│   │   ├── AllProductFrame.java
│   │   ├── CartFrame.java
│   │   ├── ForgodPasswordFrame.java
│   │   ├── HomeFrame.java
│   │   ├── LoginFrame.java
│   │   ├── ManageProductsFrame.java
│   │   ├── OrderFrame.java
│   │   ├── SignUpFrame.java
│   │   └── ViewOrdersFrame.java
│   └── model/
│       ├── Admin.java
│       ├── AdminDao.java
│       ├── Calculate.java
│       ├── Dao.java
│       ├── MyConnection.java
│       ├── Payment.java
│       ├── Product.java
│       └── cart.java
├── build.xml
└── README.md
```

## Features Details

### Tax Calculation
Automatic tax calculation based on subtotal ranges:
- $10.00 - $20.00: $0.50
- $20.01 - $30.00: $1.00
- $30.01 - $40.00: $1.50
- $40.01 - $60.00: $2.00
- $60.01 - $80.00: $3.00
- $80.01 - $100.00: $4.00
- $100.01 - $150.00: $8.00
- $150.01 - $200.00: $8.00
- Over $200.00: $10.00

### Security Features
- Password masking with show/hide toggle
- Security question-based password recovery
- Username validation (no numbers allowed)
- Session management
- Duplicate product prevention in cart

## Screenshots

The application includes the following screens:
- Login Screen
- Sign Up Screen
- Forgot Password Screen
- Home Dashboard
- Add Product Screen
- Manage Products Screen
- All Products View
- Order Screen
- Cart/Checkout Screen
- View Orders Screen

## Known Limitations

- Single admin user system (can be extended for multiple users)
- Local database only (no remote database support out of the box)
- Receipt printing uses Java's built-in print functionality
- Image storage in database (BLOB) may impact performance with many products

## Future Enhancements

- Multi-user support with role-based access control
- Cloud database integration
- Sales reports and analytics
- Inventory management with stock levels
- Barcode scanning support
- Customer loyalty program
- Email receipt functionality

## Troubleshooting

### Database Connection Issues
- Verify MySQL service is running
- Check database credentials in `MyConnection.java`
- Ensure MySQL Connector/J is properly added to the project

### Image Upload Issues
- Supported formats: PNG, JPG, JPEG
- Ensure sufficient database storage for BLOBs

### Build Issues
- Verify JDK version compatibility
- Check all dependencies are properly added
- Clean and rebuild the project

## License

This project is created for educational purposes.

## Author

Avindu

## Support

For issues or questions, please refer to the project documentation or contact the development team.
