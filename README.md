# Neptune - Competitive Programming Platform

Neptune is a web-based competitive programming platform that allows students to practice coding problems and teachers to create and manage programming exercises.

## Features

- User authentication (Student/Teacher roles)
- Programming case management
- Code submission and evaluation
- Real-time feedback
- Submission history
- Profile management

## Tech Stack

### Backend

- Go
- Gin web framework
- GORM
- PostgreSQL
- JWT authentication

### Frontend

- React
- TypeScript
- Vite
- Tailwind CSS
- DaisyUI
- Monaco Editor

## Getting Started

### Prerequisites

- Go 1.16 or later
- Node.js 16 or later
- PostgreSQL 13 or later

### Backend Setup

1. Navigate to the backend directory:

   ```bash
   cd backend
   ```

2. Install dependencies:

   ```bash
   go mod download
   ```

3. Create a `.env` file with the following variables:

   ```
   DB_HOST=localhost
   DB_PORT=5432
   DB_USER=postgres
   DB_PASSWORD=your_password
   DB_NAME=neptune
   JWT_SECRET=your_jwt_secret
   ```

4. Run the database migrations:

   ```bash
   go run cmd/migrate/main.go
   ```

5. Start the server:
   ```bash
   go run cmd/server/main.go
   ```

The backend server will start on `http://localhost:8080`.

### Frontend Setup

1. Navigate to the frontend directory:

   ```bash
   cd frontend
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```

The frontend development server will start on `http://localhost:5173`.

## API Documentation

### Authentication

#### Login

```
POST /api/auth/login
Content-Type: application/json

{
  "username": "string",
  "password": "string"
}
```

#### Register

```
POST /api/auth/register
Content-Type: application/json

{
  "username": "string",
  "email": "string",
  "password": "string",
  "role": "student" | "teacher"
}
```

### Cases

#### List Cases

```
GET /api/cases
Authorization: Bearer <token>
```

#### Get Case

```
GET /api/cases/:id
Authorization: Bearer <token>
```

#### Create Case (Teacher only)

```
POST /api/cases
Authorization: Bearer <token>
Content-Type: application/json

{
  "title": "string",
  "description": "string",
  "header": "string",
  "isPublic": boolean,
  "classId": "string",
  "testCases": [
    {
      "input": "string",
      "output": "string",
      "isHidden": boolean
    }
  ]
}
```

### Submissions

#### Submit Code

```
POST /api/submissions
Authorization: Bearer <token>
Content-Type: application/json

{
  "caseId": number,
  "code": "string",
  "language": "C" | "Python"
}
```

#### List Submissions

```
GET /api/submissions
Authorization: Bearer <token>
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
