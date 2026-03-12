# Node Express EJS Blog App

A simple yet functional blog application built with Node.js, Express, MongoDB, and EJS templating. Features full CRUD operations for managing blog posts with a clean, responsive interface.

## Features

- **Create** - Add new blog posts with title, image, and body content
- **Read** - View all blog posts in a list or individual post details
- **Update** - Edit existing blog posts
- **Delete** - Remove blog posts
- Input sanitization for security
- Responsive design with custom CSS
- Docker support for easy deployment

## Tech Stack

| Component | Technology |
|-----------|------------|
| Backend | Node.js + Express |
| Database | MongoDB + Mongoose |
| Templating | EJS (Embedded JavaScript) |
| Styling | Custom CSS |
| Containerization | Docker + Docker Compose |

## Project Structure

```
Node-Express-EJS-CRUD/
├── app.js                 # Main application entry point
├── package.json           # Dependencies and scripts
├── dockerfile             # Docker configuration for Node app
├── docker-compose.yml     # Multi-container orchestration
├── public/
│   └── stylesheet/
│       └── app.css        # Custom styles
└── views/
    ├── index.ejs          # Blog listing page
    ├── show.ejs           # Single blog post view
    ├── new.ejs            # Create new post form
    ├── edit.ejs           # Edit post form
    └── partials/
        ├── header.ejs     # Common header template
        └── footer.ejs     # Common footer template
```

## Requirements

- [Node.js](https://nodejs.org/) (v11+ recommended)
- [MongoDB](https://www.mongodb.com/) (local or Docker)
- [Docker](https://www.docker.com/) & Docker Compose (optional)

## Installation

### Option 1: Docker (Recommended)

```bash
# Clone and navigate to the project
cd Node-Express-EJS-CRUD

# Start containers
docker-compose up

# Access the app at http://localhost:3000
```

### Option 2: Local Development

```bash
# Install dependencies
npm install

# Start MongoDB locally (ensure it's running on port 27017)

# Run the application
node app.js

# Or use nodemon for auto-restart during development
npx nodemon app.js

# Access the app at http://localhost:3000
```

## API Routes

| Method | Route | Description |
|--------|-------|-------------|
| GET | `/` | Redirects to `/blogs` |
| GET | `/blogs` | List all blog posts |
| GET | `/blogs/new` | Form to create new post |
| POST | `/blogs` | Create new blog post |
| GET | `/blogs/:id` | Show single blog post |
| GET | `/blogs/:id/edit` | Form to edit post |
| PUT | `/blogs/:id` | Update blog post |
| DELETE | `/blogs/:id` | Delete blog post |

## Data Model

**Blog Schema:**
- `title` (String) - Post title
- `image` (String) - Image URL (defaults to placeholder)
- `body` (String) - Post content
- `created` (Date) - Creation timestamp (auto-generated)

## Configuration

The app connects to MongoDB at `mongodb://mongo:27017/myBlog-DB` (Docker) or your local MongoDB instance. To change the database connection, edit the connection string in `app.js`:

```javascript
mongoose.connect('mongodb://localhost:27017/myBlog-DB', {
  useNewUrlParser: true,
  useCreateIndex: true,
  useFindAndModify: false
});
```