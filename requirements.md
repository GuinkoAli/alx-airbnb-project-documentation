# Airbnb Clone - Backend Requirement Specifications

This document outlines the technical requirements for key backend features of the Airbnb Clone project.

## 1. User Authentication

### Overview
The authentication system will handle user registration, login, and session management using JWT tokens.

### API Endpoints

#### POST /api/auth/register
- **Description**: Register a new user
- **Request Body**:
  ```json
  {
    "email": "user@example.com",
    "password": "SecurePassword123!",
    "first_name": "John",
    "last_name": "Doe",
    "role": "guest" // or "host"
  }
'''


  #### POST /api/auth/properties
- **Description**: Create a new property
- **Request Body**:
 ```json
{
  "title": "Beautiful Beach House",
  "description": "A lovely beachfront property with amazing views",
  "location": "Miami Beach, FL",
  "price_per_night": 150.00,
  "bedrooms": 2,
  "bathrooms": 1,
  "max_guests": 4,
  "amenities": ["wifi", "pool", "parking"]
}


{
  "id": "property-uuid",
  "title": "Beautiful Beach House",
  "description": "A lovely beachfront property with amazing views",
  "location": "Miami Beach, FL",
  "price_per_night": 150.00,
  "bedrooms": 2,
  "bathrooms": 1,
  "max_guests": 4,
  "amenities": ["wifi", "pool", "parking"],
  "host_id": "user-uuid",
  "created_at": "2023-07-15T10:30:00Z",
  "updated_at": "2023-07-15T10:30:00Z"
}
```


#### POST /api/abooking
- **Description**: Create a new booking
- **Header**: Authorization: Bearer<token>
- **Request Body**:
```json
{
  "property_id": "property-uuid",
  "start_date": "2023-08-01",
  "end_date": "2023-08-05",
  "guests": 2
}
{
  "id": "booking-uuid",
  "property_id": "property-uuid",
  "user_id": "user-uuid",
  "start_date": "2023-08-01",
  "end_date": "2023-08-05",
  "guests": 2,
  "total_price": 600.00,
  "status": "pending",
  "created_at": "2023-07-15T10:30:00Z"
}
 ```



#### POST /api/abooking/:id
- **Description**: Get booking details
- **Header**: Authorization: Bearer<token>
- ** Response**:
 ```json
 {
  "id": "booking-uuid",
  "property": {
    "id": "property-uuid",
    "title": "Beautiful Beach House",
    "location": "Miami Beach, FL"
  },
  "user": {
    "id": "user-uuid",
    "first_name": "John",
    "last_name": "Doe"
  },
  "start_date": "2023-08-01",
  "end_date": "2023-08-05",
  "guests": 2,
  "total_price": 600.00,
  "status": "confirmed",
  "created_at": "2023-07-15T10:30:00Z"
}