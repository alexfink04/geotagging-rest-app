# GeoTagging & Spatial Discovery Web Application

A lightweight, full-stack JavaScript application designed to create, manage, and discover geographically tagged locations ("GeoTags"). This project implements a robust Node.js/Express REST API in the backend paired with a dynamic, event-driven vanilla JavaScript frontend utilizing interactive mapping services.

##  Core Features

* **HTML5 Geolocation Integration:** Automatically retrieves the user's current device location via browser APIs to center the application interface.
* **Interactive Map UI:** Integrated with **Leaflet.js** and OpenStreetMap to display live markers for the user's current location and nearby saved tags.
* **Full RESTful API Architecture:** Implements standard HTTP methodologies (`GET`, `POST`, `PUT`, `DELETE`) for complete CRUD operations on location data.
* **Advanced Server-Side Filtering:** Features location-aware querying, enabling radius/nearby searches combined with keyword matching for hashtags and names.
* **Custom Pagination:** Efficient server-side data chunking (pagination) to optimize payload delivery and frontend rendering performance.

##  Architecture & File Structure

* `routes/index.js` - The central Express Router handling API endpoints and server-side logic (filtering, pagination, CRUD operations).
* `geotagging.js` - Main client-side script managing DOM interaction, form submissions, asynchronous API scheduling (`fetch`), and pagination state.
* `LocationHelper.js` - Encapsulated helper class wrapping the native HTML5 Geolocation API with secure private fields (`#latitude`, `#longitude`).
* `MapManager.js` - Wrapper class managing the Leaflet map instance, handling layer resets, custom icons, and dynamic marker population.

##  Technology Stack

* **Backend:** Node.js, Express.js
* **Frontend:** Vanilla JavaScript (ES6+), HTML5, CSS3
* **Mapping Service:** Leaflet.js, OpenStreetMap
* **Data Format:** JSON

##  REST API Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/geotags` | Retrieves GeoTags (supports `latitude`, `longitude`, `searchterm`, `page`, `limit` queries) |
| `POST` | `/api/geotags` | Creates a new GeoTag resource |
| `GET` | `/api/geotags/:id` | Fetches a single specific GeoTag by its ID |
| `PUT` | `/api/geotags/:id` | Updates an existing GeoTag's data fields |
| `DELETE` | `/api/geotags/:id` | Removes a specific GeoTag from the data store |

##  Local Setup & Installation

1. Clone the repository:
   ```bash
   git clone [https://github.com/alexfink04/geotagging-rest-app.git](https://github.com/alexfink04/geotagging-rest-app.git)
   cd geotagging-rest-app

2. Install dependencies: Since the heavy `node_modules` folder is excluded from this repository via `.gitignore`,
   you need to restore all required packages (like Express). Node.js will automatically read the `package.json` file and fetch everything you need with a single command:

   `npm install`

3. Start the application: Boot up the local backend server using the predefined npm start script:

   `npm start`

5. Access the app: Once the terminal indicates that the server is running, open your preferred web browser and navigate to the local hosting address:

   `http://localhost:3000`
