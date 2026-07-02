# GeoTag Application

A full-stack web application for creating, discovering, and managing location-based tags (GeoTags) with a RESTful API backend and interactive frontend.

**Version**: 2.1.0

---

##  Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [License](#license)

---

##  Features

- **Interactive Map-Based Tagging**: Create and discover location-based tags on an interactive map
- **Full RESTful API**: Complete REST API for programmatic access to GeoTags
- **Geolocation Search**: Find tags within a specific radius of coordinates
- **Text Search**: Search tags by name or hashtag
- **Pagination Support**: Efficiently handle large datasets with built-in pagination
- **In-Memory Data Store**: Fast, simple data persistence during session
- **Example Data**: Pre-loaded example tags for demonstration purposes
- **Responsive Design**: Modern, user-friendly interface

---

##  Technology Stack

### Backend
- **Node.js**: JavaScript runtime environment
- **Express.js**: Web application framework
- **EJS**: Embedded JavaScript templating engine
- **Morgan**: HTTP request logging middleware

### Frontend
- **HTML5**: Markup structure
- **CSS3**: Styling
- **JavaScript**: Interactive functionality

### Development Tools
- **Nodemon**: Automatic server restart on file changes
- **npm**: Dependency management

---

##  Project Structure

```
gta_v4/
├── bin/
│   └── www                          # Application entry point
├── models/
│   ├── geotag.js                   # GeoTag class definition
│   ├── geotag-store.js             # In-memory data store
│   └── geotag-examples.js          # Example data
├── routes/
│   └── index.js                    # API and application routes
├── views/
│   ├── index.ejs                   # Main page template
│   └── error.ejs                   # Error page template
├── public/
│   ├── javascripts/
│   │   ├── geotagging.js           # Main application logic
│   │   ├── location-helper.js      # Geolocation utilities
│   │   └── map-manager.js          # Map interaction handler
│   └── stylesheets/
│       └── style.css               # Application styles
├── api-tests/
│   └── test.http                   # HTTP API test requests
├── app.js                          # Express app configuration
└── package.json                    # Project dependencies
```

---

##  Installation

### Prerequisites
- Node.js (v12 or higher)
- npm (Node Package Manager)

### Steps

1. **Clone or download the project**
   ```bash
   cd Geotagging_App/gta_v4
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm start
   ```
   The server will start at `http://localhost:3000` with automatic reload on file changes.

---

## Usage

### Web Interface
1. Open your browser and navigate to `http://localhost:3000`
2. **Create a GeoTag**: 
   - Enter location coordinates (latitude, longitude)
   - Provide a place name
   - Add an optional hashtag
   - Submit the form
3. **Discover Tags**:
   - Enter your coordinates
   - Optionally search by keyword
   - View nearby tags or search results

### API Integration

The application provides a complete REST API for programmatic access. See the [API Documentation](#api-documentation) section below.

---

## 🔌 API Documentation

### Base URL
```
http://localhost:3000/api
```

### Endpoints

#### GET /geotags
Retrieve all GeoTags or search with filters.

**Query Parameters:**
- `searchterm` (optional): Search by tag name or hashtag
- `latitude` (optional): Latitude for location-based search
- `longitude` (optional): Longitude for location-based search
- `page` (optional): Page number for pagination (default: 1)
- `limit` (optional): Results per page (default: 5)

**Response:**
```json
{
  "tags": [
    {
      "_id": 1,
      "name": "HKA Campus",
      "latitude": 49.0134,
      "longitude": 8.4040,
      "hashtag": "#university"
    }
  ],
  "pagination": {
    "current": 1,
    "pages": 3,
    "total": 15,
    "limit": 5
  }
}
```

#### POST /geotags
Create a new GeoTag.

**Request Body:**
```json
{
  "name": "Coffee Shop",
  "latitude": 49.0140,
  "longitude": 8.4050,
  "hashtag": "#coffee"
}
```

**Response:** `201 Created`
Returns the created GeoTag with assigned ID.

#### GET /geotags/:id
Retrieve a specific GeoTag by ID.

**Response:** `200 OK` or `404 Not Found`

#### PUT /geotags/:id
Update a specific GeoTag.

**Request Body:**
```json
{
  "name": "Updated Name",
  "latitude": 49.0140,
  "longitude": 8.4050,
  "hashtag": "#updated"
}
```

**Response:** `200 OK` with updated GeoTag or `404 Not Found`

#### DELETE /geotags/:id
Delete a specific GeoTag.

**Response:** `200 OK` with deleted GeoTag or `404 Not Found`

---

##  Example Requests

You can test the API using the included `api-tests/test.http` file or use tools like:
- **curl**
- **Postman**
- **VS Code REST Client Extension**

Example with curl:
```bash
# Get all tags
curl http://localhost:3000/api/geotags

# Create a new tag
curl -X POST http://localhost:3000/api/geotags \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Local Landmark",
    "latitude": 49.01,
    "longitude": 8.40,
    "hashtag": "#landmark"
  }'

# Search nearby tags
curl "http://localhost:3000/api/geotags?latitude=49.01&longitude=8.40&searchterm=coffee"
```

---

##  Development

### Available Scripts

- `npm start` - Start the development server with auto-reload

### Key Features of the Implementation

- **Pagination**: Efficient handling of large datasets with configurable page size
- **Geolocation Search**: Proximity-based filtering using latitude/longitude coordinates
- **Text Search**: Case-insensitive searching across tag names and hashtags
- **Error Handling**: Comprehensive error responses with appropriate HTTP status codes
- **Data Validation**: Input validation for numeric coordinates

---

##  License

This project is part of the VS1LAB course exercises. Please refer to the [LICENSE](../LICENSE) file in the project root for details.

---

##  Contact

This application was developed as part of university coursework for the VS1LAB program.

---

##  Learning Outcomes

This project demonstrates:
- RESTful API design and implementation
- Full-stack web application development
- Express.js framework usage
- Client-side JavaScript programming
- Geolocation and map-based features
- Pagination and data filtering
- HTTP methods (GET, POST, PUT, DELETE)
- JSON data handling

