require("dotenv").config();

const express = require("express");
const mysql = require("mysql");

const app = express();
const port = process.env.PORT || 5000;

// Database connection
const db = mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: "electricity_bills",
});

db.connect((err) => {
  if (err) {
    console.error("Database connection failed:", err);
  } else {
    console.log("Database connected!");
  }
});

app.listen(port, () => console.log(`Server running on port ${port}`));
