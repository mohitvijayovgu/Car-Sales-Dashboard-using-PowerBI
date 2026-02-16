# Car Sales Dataset

## Overview
The Classic Models Dataset is a comprehensive sample database containing sales information for a model car company. This dataset includes customer data, orders, products, employees, office locations, and payment records. It's commonly used for learning and demonstrating database design, SQL queries, data analysis, and business intelligence concepts.

## Dataset Structure

### File Descriptions

#### **customers.csv**
Contains customer account information and contact details.

**Columns:**
- `customerNumber` - Unique customer identifier (Primary Key)
- `customerName` - Company name of the customer
- `contactLastName` - Last name of primary contact
- `contactFirstName` - First name of primary contact
- `phone` - Customer phone number
- `addressLine1` - Primary address line
- `addressLine2` - Secondary address line (may be NULL)
- `city` - City of customer location
- `state` - State/Province (may be NULL)
- `postalCode` - Postal/Zip code
- `country` - Country
- `salesRepEmployeeNumber` - Employee ID of assigned sales representative (Foreign Key)
- `creditLimit` - Maximum credit limit for the customer

**Records:** 123 customers

---

#### **orders.csv**
Contains order header information and status tracking.

**Columns:**
- `orderNumber` - Unique order identifier (Primary Key)
- `orderDate` - Date the order was placed
- `requiredDate` - Date the customer requires the order
- `shippedDate` - Date the order was shipped (may be NULL if not yet shipped)
- `status` - Current order status (e.g., Shipped, Cancelled, On Hold, Disputed)
- `comments` - Any additional notes about the order (may be NULL)
- `customerNumber` - Customer ID (Foreign Key to customers)

**Records:** 327 orders

---

#### **order details.csv**
Contains line item details for each order. One order can have multiple line items.

**Columns:**
- `orderNumber` - Order identifier (Foreign Key to orders)
- `productCode` - Product identifier (Foreign Key to products)
- `quantityOrdered` - Quantity of this product in the order
- `priceEach` - Unit price for this product in this order
- `orderLineNumber` - Sequential line number within the order

**Records:** 2,997 order line items

---

#### **products.csv**
Contains product catalog information including inventory and pricing.

**Columns:**
- `productCode` - Unique product identifier (Primary Key)
- `productName` - Name/description of the product
- `productLine` - Category/line the product belongs to (Foreign Key to productlines)
- `productVendor` - Manufacturer or vendor name
- `productDescription` - Detailed description of the product
- `quantityInStock` - Current inventory quantity
- `buyPrice` - Cost price (what the company pays)
- `MSRP` - Manufacturer's Suggested Retail Price

**Records:** 119 products

---

#### **productlines.csv**
Contains product category/line information.

**Columns:**
- `productLine` - Product line identifier (Primary Key)
- `textDescription` - Text description of the product line
- `htmlDescription` - HTML-formatted description (may be NULL)
- `image` - Image reference/path (may be NULL)

**Records:** 9 product lines
- Classic Cars
- Motorcycles
- Planes
- Ships
- Trains
- Trucks and Buses
- Vintage Cars
- Special Edition
- And more...

---

#### **employees.csv**
Contains employee information and organizational hierarchy.

**Columns:**
- `employeeNumber` - Unique employee identifier (Primary Key)
- `lastName` - Employee's last name
- `firstName` - Employee's first name
- `extension` - Phone extension
- `email` - Email address
- `officeCode` - Office location (Foreign Key to offices)
- `reportsTo` - Employee ID of direct manager (may be NULL for top-level)
- `jobTitle` - Job position/title

**Records:** 24 employees

---

#### **offices.csv**
Contains office location information.

**Columns:**
- `officeCode` - Unique office identifier (Primary Key)
- `city` - City where office is located
- `phone` - Office phone number
- `addressLine1` - Primary address line
- `addressLine2` - Secondary address line (may be NULL)
- `state` - State/Province (may be NULL)
- `country` - Country
- `postalCode` - Postal/Zip code
- `territory` - Geographic sales territory

**Records:** 8 offices
- North America (NA)
- Europe (EMEA)
- Asia-Pacific (APAC)

---

#### **payments.csv**
Contains payment transaction records from customers.

**Columns:**
- `customerNumber` - Customer ID (Foreign Key to customers)
- `checkNumber` - Check or payment reference number
- `paymentDate` - Date payment was received
- `amount` - Payment amount

**Records:** 274 payment transactions

---

## Entity Relationship

```
offices ──────────────► employees
  │                        │
  │                        └──► customers ◄──────┐
  └─────────────────────────────────────────────┘

customers ──────────────► orders ──────────────► order details
                                                      │
                                                      v
                                              products ◄────┐
                                                      │      │
                                                 productlines
customers ──────────────► payments
```

## Usage Examples

### Key Relationships
1. **Customers to Orders**: Each customer can place multiple orders (1:M)
2. **Orders to Order Details**: Each order contains multiple line items (1:M)
3. **Products to Order Details**: Each product can appear in multiple orders (1:M)
4. **Employees to Customers**: Each sales representative manages multiple customers (1:M)
5. **Employees to Offices**: Multiple employees work at each office (M:1)
6. **Products to Product Lines**: Each product belongs to one product line (M:1)

### Analysis Opportunities
- Calculate total sales revenue by customer, region, or product line
- Track order fulfillment status and delivery times
- Analyze product inventory levels and sales performance
- Examine payment patterns and outstanding receivables
- Build organizational hierarchy and sales team structures
- Identify top-performing products, employees, and customer accounts

## Data Quality Notes
- Some fields contain NULL values (indicated as "NULL" in CSV files)
- All dates are in YYYY-MM-DD format
- Currency amounts appear to be in USD
- Phone numbers follow various international formats
- The dataset represents a fictional company for training purposes

## File Format
- **Format**: CSV (Comma-Separated Values)
- **Encoding**: UTF-8

## Last Updated
February 2026

---

For data analysis and visualization, these CSV files can be imported into:
- Microsoft Power BI (as included in the classicalmodels.pbix file)
- SQL Databases
- Excel
- Business Intelligence tools
- Data analysis platforms
