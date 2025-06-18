# Housing Agent Backend - API Reference

## 🚀 Quick Start
```bash
npm start
# Server runs on http://localhost:3000
```

## 📋 API Endpoints

### 🔐 Authentication

#### Register User
```http
POST /api/register
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "password123",
  "userType": "agent" | "client"
}
```

#### Login User
```http
POST /api/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "password123"
}
```

### 🏠 Property Listings

#### Get All Listings
```http
GET /api/listings
```

#### Create New Listing
```http
POST /api/listings
Content-Type: multipart/form-data

{
  "title": "Modern Apartment",
  "location": "Lekki, Lagos",
  "price": 25000000,
  "description": "Beautiful apartment",
  "latitude": 6.5244,
  "longitude": 3.3792,
  "images": [file1, file2, ...], // up to 5 images
  "documents": [file1, file2, ...] // up to 3 documents
}
```

### 💬 Chat System

#### Get Chat Messages
```http
GET /api/chat
```

#### Send Message
```http
POST /api/chat
Content-Type: application/json

{
  "text": "Hello, I'm interested in the apartment"
}
```

## 📁 File Structure
```
backend/
├── server.js          # Main server file
├── package.json       # Dependencies
├── users.json         # User data
├── listings.json      # Property listings
├── chat.json          # Chat messages
└── uploads/           # Uploaded files
```

## 🔧 Sample Data

### Existing Users
- `omotosomarytaiwo@gmail.com` (client)
- `omartprncx@gmail.com` (agent)
- `marytaiwo@gmail.com` (client)

### Sample Listing
```json
{
  "id": 1234567890,
  "title": "Modern 3-Bedroom Apartment",
  "location": "Lekki, Lagos",
  "price": 25000000,
  "description": "Beautiful apartment with sea view",
  "latitude": 6.5244,
  "longitude": 3.3792,
  "images": [
    "http://localhost:3000/uploads/1234567890-image1.jpg"
  ],
  "documents": [
    "http://localhost:3000/uploads/1234567890-doc1.pdf"
  ]
}
```

## ⚡ Quick Demo Commands

### Test Registration
```bash
curl -X POST http://localhost:3000/api/register \
  -H "Content-Type: application/json" \
  -d '{"email":"demo@test.com","password":"test123","userType":"agent"}'
```

### Test Login
```bash
curl -X POST http://localhost:3000/api/login \
  -H "Content-Type: application/json" \
  -d '{"email":"omotosomarytaiwo@gmail.com","password":"password123"}'
```

### Get Listings
```bash
curl http://localhost:3000/api/listings
```

### Send Chat Message
```bash
curl -X POST http://localhost:3000/api/chat \
  -H "Content-Type: application/json" \
  -d '{"text":"Hello, I need an apartment"}'
```

## 🎯 Demo Flow Checklist
- [ ] Start server
- [ ] Show package.json dependencies
- [ ] Demonstrate user registration
- [ ] Demonstrate user login
- [ ] Show empty listings
- [ ] Create new listing with files
- [ ] Show created listing
- [ ] Demonstrate chat system
- [ ] Show data persistence
- [ ] Highlight security features 