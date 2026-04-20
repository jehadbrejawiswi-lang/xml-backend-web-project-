# XML Product Catalog

This project is an e-commerce product catalog system that uses XML for data storage and demonstrates various XML technologies and web services techniques.

## Project Overview

The project consists of two parts:
1. **Backend API** - A C# ASP.NET Core API that works with XML data
2. **Frontend Client** - A React.js application that consumes the API

## XML Features Demonstrated

- **XML document creation and manipulation**
- **XML validation using both DTD and XSD**
- **XML Schema with data types, patterns, and constraints**
- **XSLT transformation** (XML to HTML)
- **XML parsing techniques** (DOM and XPath)
- **XML serialization and deserialization**

## Web Service Features

- **RESTful API design**
- **Content negotiation** (JSON and XML)
- **JWT authentication**
- **HTTP request methods** (GET, POST, PUT, DELETE)
- **XML-based web services**

## Technology Stack

### Backend
- **ASP.NET Core 8**
- **C# XML APIs** (XmlDocument, XmlSerializer, XPath, XSLT)
- **ASP.NET Core Identity** for authentication
- **JWT** for token-based auth
- **Entity Framework Core** for user data

### Frontend
- **React.js**
- **React Bootstrap**
- **Axios** for API communication

## Getting Started

### Prerequisites
- .NET SDK 8.0+
- SQL Server (LocalDB is sufficient for development)
- Node.js and npm

### Backend Setup
1. Navigate to the `xmlproject` directory
2. Update connection string in `appsettings.json` if needed
3. Apply EF Core migrations:
```
dotnet ef database update
```
4. Run the API:
```
dotnet run
```

### Frontend Setup
1. Navigate to the `product-catalog-client` directory
2. Install dependencies:
```
npm install
```
3. Run the React app:
```
npm start
```

## Architecture

The solution follows a layered architecture:
- **Controllers** - Handle HTTP requests and responses
- **Models** - Define data structures with XML serialization attributes
- **Repositories** - Manage XML data operations
- **Services** - Provide authentication and other utilities

## XML Data Structure

The product catalog is stored in XML format with:
- Product information (name, description, price, etc.)
- Categories and subcategories
- Product specifications
- Images
- Ratings

The XML documents are validated using both DTD and XSD schemas to ensure data integrity.

## Authentication

The system uses JWT-based authentication:
1. User registers/logs in through the API
2. Server generates a JWT token
3. Client stores token and sends it with authenticated requests
4. Server validates token for protected operations

## Key Features

- **XML Data Management**: Create, read, update, and delete products in XML format
- **XML Validation**: Validate XML against DTD and XSD schemas
- **XSLT Transformation**: Transform product data into HTML for display
- **Content Negotiation**: API can serve both JSON and XML formats
- **Authentication**: Secure product management operations with JWT
- **Responsive UI**: Clean, user-friendly interface for the product catalog

## API Documentation

### Authentication

#### Register
- **POST** `/api/auth/register`
- **Request Body (JSON):**
```json
{
  "email": "user@example.com",
  "username": "yourusername",
  "password": "YourPassword123!",
  "confirmPassword": "YourPassword123!"
}
```
- **Response (Success):**
```json
{
  "success": true,
  "token": "<JWT token>",
  "email": "user@example.com",
  "userId": "1",
  "message": "User registered successfully."
}
```
- **Response (Error):**
```json
{
  "success": false,
  "message": "Username already registered."
}
```

#### Login
- **POST** `/api/auth/login`
- **Request Body (JSON):**
```json
{
  "email": "user@example.com", // or
  "username": "yourusername",
  "password": "YourPassword123!"
}
```
- **Response (Success):**
```json
{
  "success": true,
  "token": "<JWT token>",
  "email": "user@example.com",
  "userId": "1",
  "message": "Login successful."
}
```
- **Response (Error):**
```json
{
  "success": false,
  "message": "Invalid username/email or password."
}
```

### Products

#### Get All Products
- **GET** `/api/products`
- **Headers:** `Authorization: Bearer <token>` (if protected)
- **Response:**
```json
[
  {
    "id": "1",
    "name": "Product 1",
    "description": "...",
    // ...
  },
  // ...
]
```

#### Get Product by ID
- **GET** `/api/products/{id}`
- **Headers:** `Authorization: Bearer <token>` (if protected)
- **Response:**
```json
{
  "id": "1",
  "name": "Product 1",
  "description": "..."
  // ...
}
```

#### Example curl Request
```sh
curl -X POST https://localhost:7256/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"user@example.com","password":"YourPassword123!"}'
```

---

For more endpoints, see the controllers or ask for more details. 