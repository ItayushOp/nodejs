// app.js - Node.js server for a browser-based code editor

const express = require('express');
const path = require('path');
const fs = require('fs');

const app = express();
const PORT = 3000;

// Serve static files from the 'public' directory
app.use(express.static(path.join(__dirname, 'public')));

// Middleware to parse JSON data
app.use(express.json());

// Endpoint to save files
app.post('/save', (req, res) => {
  const { filename, content } = req.body;

  if (!filename || !content) {
    return res.status(400).send('Filename and content are required.');
  }

  const filePath = path.join(__dirname, 'files', filename);

  fs.writeFile(filePath, content, (err) => {
    if (err) {
      console.error(err);
      return res.status(500).send('Failed to save the file.');
    }
    res.send('File saved successfully.');
  });
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server is running at http://localhost:${PORT}`);
});
