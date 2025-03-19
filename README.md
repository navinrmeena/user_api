# User Authentication and Profile Management API

This project provides a complete authentication and profile management API, including features such as user registration, login, logout, password change, profile updates, avatar/cover image uploads, and more.

---

## 🚀 Features

- **User Authentication**
  - Register with avatar and cover image upload
  - Login with email/username and password
  - JWT-based authentication with access and refresh tokens
  - Logout and invalidate refresh tokens

- **User Profile Management**
  - Update account details (full name, email)
  - Change current password
  - Get current user profile
  - Update avatar and cover image
  - Get user channel profile with subscriber and subscription details
  - Fetch watch history with associated videos

- **Token Management**
  - Generate and refresh access/refresh tokens
  - Secure cookies for token storage

---






## ⚡️ API Endpoints

### 🔐 Authentication Routes

| Method | Endpoint             | Description                       | Middleware    |
|--------|----------------------|-----------------------------------|---------------|
| POST   | `/api/v1/register`    | Register a new user               | `upload`      |
| POST   | `/api/v1/login`       | Login user                        | None          |
| POST   | `/api/v1/logout`      | Logout user                       | `verifyJWT`   |
| POST   | `/api/v1/refresh-token` | Refresh access token            | None          |
| POST   | `/api/v1/change-password` | Change user password           | `verifyJWT`   |
| GET    | `/api/v1/current-user` | Get current user details         | `verifyJWT`   |

### 📝 Profile Management Routes

| Method | Endpoint             | Description                       | Middleware    |
|--------|----------------------|-----------------------------------|---------------|
| PATCH  | `/api/v1/update-account` | Update account details         | `verifyJWT`   |
| PATCH  | `/api/v1/avatar`      | Update user avatar                | `verifyJWT`, `upload.single` |
| PATCH  | `/api/v1/cover-image` | Update user cover image           | `verifyJWT`, `upload.single` |
| GET    | `/api/v1/c/:username` | Get user channel profile          | `verifyJWT`   |
| GET    | `/api/v1/history`     | Get user watch history            | `verifyJWT`   |

---

## 🛠️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-repo/user-auth-api.git
cd user-auth-api
```
### 2. Install dependencies
```bash
# Using npm
npm install

# OR using yarn
yarn install

```

### 3. Setup environment variables
Create a .env file in the root directory and configure the following:
```bash
PORT=5000
MONGODB_URI=mongodb://localhost:27017/user-auth-db
ACCESS_TOKEN_SECRET=your-access-token-secret
REFRESH_TOKEN_SECRET=your-refresh-token-secret
CLOUDINARY_CLOUD_NAME=your-cloudinary-cloud-name
CLOUDINARY_API_KEY=your-cloudinary-api-key
CLOUDINARY_API_SECRET=your-cloudinary-api-secret
```

### 4. Run the server
```bash
# Development mode
npm run dev

# OR using yarn
yarn dev
```

## 📡 API Usage

### Register User
``POST /api/v1/register
``
#### Request Body (Form Data)
```json
{
  "fullName": "John Doe",
  "email": "john@example.com",
  "username": "john_doe",
  "password": "securepassword"
}

```
####  Response
```json
{
  "status": 200,
  "data": {
    "_id": "userId",
    "fullName": "John Doe",
    "email": "john@example.com",
    "username": "john_doe",
    "avatar": "avatar-url",
    "coverImage": "cover-image-url"
  },
  "message": "User registered Successfully"
}


```

### Login User
``POST /api/v1/login
``
#### Request Body (Form Data)
```json
{
  "email": "john@example.com",
  "password": "securepassword"
}

```
####  Response
```json
{
  "status": 200,
  "data": {
    "user": {
      "_id": "userId",
      "fullName": "John Doe",
      "email": "john@example.com",
      "username": "john_doe",
      "avatar": "avatar-url"
    },
    "accessToken": "access-token",
    "refreshToken": "refresh-token"
  },
  "message": "User logged In Successfully"
}


```

### Refresh Access Token
``POST /api/v1/refresh-token
``
#### Request Body (Form Data)
```json
{
  "refreshToken": "valid-refresh-token"
}


### Update Account Details
``PATCH /api/v1/update-account
``
#### Request Body (Form Data)
```json
{
  "fullName": "John Updated",
  "email": "john_updated@example.com"
}



### Change Password
``POST /api/v1/change-password
``
#### Request Body (Form Data)
```json
{
  "oldPassword": "securepassword",
  "newPassword": "newpassword"
}


```


## 📧 Contact
For any inquiries or issues, feel free to reach out:

Email: navinrmeena13@gmail.com

GitHub: https://github.com/navinrmeena

Happy Coding! 🎉
