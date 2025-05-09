**1. User Authentication**
This module handles user registration, login, and authentication via token-based sessions.

**Endpoints**
1.1 POST /api/auth/register
    **Description**: Registers a new user account.

    **Input(JSON):**
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "password": "StrongPass123!",
  "phone_number": "1234567890",
  "role": "guest"
}

**Output (Success – 201):**

{
  "message": "User registered successfully.",
  "user_id": "uuid-value",
  "token": "jwt-token"
}


**Validations**:
Email: valid format, unique

Password: minimum 8 characters, must include a number and special character

Role: must be one of guest, host, or admin

**1.2 POST /api/auth/login**

**Description**: Authenticates user and issues JWT token.

**Input (JSON):**
{
  "email": "john@example.com",
  "password": "StrongPass123!"
}

**Output (Success – 200):**

{
  "token": "jwt-token",
  "user_id": "uuid-value"
}

**Validations:**
Email exists
Password matches hash

**Performance Criteria**
Token generation should complete in < 200ms
Registration should complete in < 500ms
Support 100 concurrent login requests per second

