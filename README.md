
# Blog Platform Backend

A robust RESTful API backend for the Blog Platform application built with Node.js, Express, and MongoDB.

## Features

- **Authentication & Authorization**: Secure JWT-based authentication system
- **User Management**: User registration, login, and profile management
- **Blog Management**: CRUD operations for blog posts with image uploads
- **Category System**: Organize blogs with categories
- **Author Management**: Track and manage blog authors
- **Comment System**: Allow users to comment on blog posts
- **Search & Filtering**: Advanced search and filtering capabilities
- **Pagination**: Efficient data loading with pagination
- **Data Validation**: Input validation for all API endpoints
- **Error Handling**: Comprehensive error handling and logging

## Technologies Used

- **Node.js**: JavaScript runtime
- **Express**: Web framework for Node.js
- **MongoDB**: NoSQL database
- **Mongoose**: MongoDB object modeling
- **JWT**: JSON Web Tokens for authentication
- **Multer**: File upload middleware
- **Bcrypt**: Password hashing
- **Cors**: Cross-Origin Resource Sharing

## Setup Instructions

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or Atlas)

### Installation

1. Clone the repository
2. Navigate to the backend directory:
   ```
   cd backend
   ```
3. Install dependencies:
   ```
   npm install
   ```

### Configuration

Create a `.env` file in the root directory with the following variables:
```
PORT=3000
NODE_ENV=development
MONGODB_URI=mongodb://localhost:27017/blog-platform
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRES_IN=30d
CORS_ORIGIN=http://localhost:5173
UPLOAD_PATH=./uploads
```

### Development

Start the development server:
```
npm run dev
```

The API will be available at `http://localhost:3000`

## API Endpoints

### Authentication
- `POST /api/auth/signup` - Register a new user
- `POST /api/auth/login` - Login and get authentication token
- `GET /api/auth/verify` - Verify JWT token

### Blogs
- `GET /api/blogs` - Get all blogs with pagination
- `GET /api/blogs/:id` - Get blog by ID
- `GET /api/blogs/slug/:slug` - Get blog by slug
- `GET /api/blogs/featured` - Get featured blogs
- `POST /api/blogs` - Create a new blog (admin only)
- `PUT /api/blogs/:id` - Update a blog (admin only)
- `DELETE /api/blogs/:id` - Delete a blog (admin only)

### Categories
- `GET /api/categories` - Get all categories
- `GET /api/categories/:id` - Get category by ID
- `GET /api/categories/slug/:slug` - Get category by slug
- `POST /api/categories` - Create a new category (admin only)
- `PUT /api/categories/:id` - Update a category (admin only)
- `DELETE /api/categories/:id` - Delete a category (admin only)

### Authors
- `GET /api/authors` - Get all authors
- `GET /api/authors/:id` - Get author by ID
- `POST /api/authors` - Create a new author (admin only)
- `PUT /api/authors/:id` - Update an author (admin only)
- `DELETE /api/authors/:id` - Delete an author (admin only)

### Users
- `GET /api/users/profile` - Get current user profile
- `PUT /api/users/profile` - Update user profile
- `GET /api/users` - Get all users (admin only)
- `PUT /api/users/:id` - Update a user (admin only)
- `DELETE /api/users/:id` - Delete a user (admin only)

### Comments
- `GET /api/blogs/:blogId/comments` - Get comments for a blog
- `POST /api/blogs/:blogId/comments` - Add a comment to a blog
- `PUT /api/comments/:id` - Update a comment (owner or admin only)
- `DELETE /api/comments/:id` - Delete a comment (owner or admin only)

## Database Models

- **User**: Authentication and user management
- **Blog**: Blog post content and metadata
- **Category**: Blog categorization
- **Author**: Author information
- **Comment**: User comments on blogs

## Running in Production

For production deployment, make sure to:
1. Set `NODE_ENV=production`
2. Use a secure JWT secret
3. Configure a production MongoDB URI
4. Set appropriate CORS settings
5. Implement rate limiting
6. Set up proper logging

## Error Handling

The API uses a consistent error response format:
```json
{
  "success": false,
  "message": "Error message",
  "error": "Error details (development only)"
}
```

## Data Validation

All API endpoints validate input data before processing. Invalid requests will receive a 400 Bad Request response with details about the validation errors.
