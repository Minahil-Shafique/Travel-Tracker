# 🌍 Travel Tracker

A web application built using **Node.js**, **Express**, and **PostgreSQL**, where users can track the countries they've visited and easily switch between user profiles. This app fetches country data from a PostgreSQL database and allows users to add new countries and users dynamically.

## 🚀 Features

- **User Management:** Create and switch between different users.
- **Track Visited Countries:** Add countries you've visited to your profile.
- **Dynamic Country Lookup:** Search and add countries to your travel history.
- **Interactive Dashboard:** View the total number of countries visited with a user-customized color theme.

## 🛠️ Tech Stack

- **Backend:** Node.js, Express
- **Database:** PostgreSQL
- **Frontend:** EJS for templating, CSS for styling
- **Other:** body-parser for handling form data, PostgreSQL as the database

## 📂 Project Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/Minahil-Shafique/Travel-Tracker.git
   ```
   ```bash
   cd Travel-Tracker
   ```
2. Install dependencies:
    ```bash
   npm install
    ```
3. Set up your PostgreSQL database:

  - Create a new database travel_tracker and adjust the credentials in server.js if necessary.<br/>
  - Ensure the following tables are present:

 ```bash
 CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  color VARCHAR(20)
);

CREATE TABLE visited_countries (
  country_code VARCHAR(3),
  user_id INTEGER REFERENCES users(id)
);

CREATE TABLE countries (
  country_code VARCHAR(3) PRIMARY KEY,
  country_name VARCHAR(100)
);
   ```
4. Start the Server:
   ```bash
   node index.js
   ```
5. Open your browser and visit http://localhost:3000.

## 📋 Endpoints

- **GET /**: Renders the main page displaying the countries visited by the current user.
- **POST /add**: Adds a new country to the visited list of the current user.
- **POST /user**: Switches between different users.
- **POST /new**: Adds a new user to the system.

## 🔧 Configuration

Ensure you update the PostgreSQL connection settings in the code if needed:

- **user**: Your PostgreSQL username (e.g., `postgres`)
- **host**: The host where your PostgreSQL server is running (e.g., `localhost`)
- **database**: The name of your PostgreSQL database (e.g., `travel_tracker`)
- **password**: Your PostgreSQL password (e.g., `password`)
- **port**: The port on which PostgreSQL is listening (default is `5432`)

Here is the example configuration in the `server.js` file:

```js
const db = new pg.Client({
  user: "postgres",       // Update with your PostgreSQL username
  host: "localhost",      // Update with your PostgreSQL host
  database: "travel_tracker", // Update with your PostgreSQL database name
  password: "password",   // Update with your PostgreSQL password
  port: 5432,             // Update with your PostgreSQL port
});

