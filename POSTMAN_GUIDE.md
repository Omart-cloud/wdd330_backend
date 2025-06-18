# Postman Guide for Housing Agent Backend API

## 🚀 Getting Started with Postman

### 1. Download and Install Postman
- Download from: https://www.postman.com/downloads/
- Install and create a free account
- Open Postman

### 2. Start Your Backend Server
```bash
cd /path/to/your/backend
npm start
# Server should be running on http://localhost:3000
```

---

## 📋 Setting Up Your Postman Collection

### Step 1: Create a New Collection
1. Click **"New"** → **"Collection"**
2. Name it: `Housing Agent Backend`
3. Add description: `API testing for real estate platform`

### Step 2: Set Up Environment Variables
1. Click **"Environments"** → **"New"**
2. Name: `Local Development`
3. Add these variables:
   - `base_url`: `http://localhost:3000`
   - `user_email`: `omotosomarytaiwo@gmail.com`
   - `user_password`: `password123`

---

## 🔐 Authentication Endpoints

### 1. User Registration
**Method**: `POST`  
**URL**: `{{base_url}}/api/register`

**Headers**:
```
Content-Type: application/json
```

**Body** (raw JSON):
```json
{
  "email": "newuser@example.com",
  "password": "securepass123",
  "userType": "agent"
}
```

**Expected Response**:
```json
{
  "message": "Registration successful"
}
```

### 2. User Login
**Method**: `POST`  
**URL**: `{{base_url}}/api/login`

**Headers**:
```
Content-Type: application/json
```

**Body** (raw JSON):
```json
{
  "email": "{{user_email}}",
  "password": "{{user_password}}"
}
```

**Expected Response**:
```json
{
  "message": "Login successful",
  "user": {
    "id": 1750078454289,
    "email": "omotosomarytaiwo@gmail.com",
    "userType": "client"
  }
}
```

---

## 🏠 Property Listings Endpoints

### 3. Get All Listings
**Method**: `GET`  
**URL**: `{{base_url}}/api/listings`

**Headers**: None required

**Expected Response**:
```json
[]
```
*(Empty array initially, will show listings after creation)*

### 4. Create New Listing (with file uploads)
**Method**: `POST`  
**URL**: `{{base_url}}/api/listings`

**Headers**: 
```
Content-Type: multipart/form-data
```

**Body** (form-data):
- `title`: `Modern 3-Bedroom Apartment`
- `location`: `Lekki, Lagos`
- `price`: `25000000`
- `description`: `Beautiful apartment with sea view and modern amenities`
- `latitude`: `6.5244`
- `longitude`: `3.3792`
- `images`: [Select files] (up to 5 images)
- `documents`: [Select files] (up to 3 documents)

**Expected Response**:
```json
{
  "message": "Listing saved",
  "listing": {
    "id": 1750081234567,
    "title": "Modern 3-Bedroom Apartment",
    "location": "Lekki, Lagos",
    "price": 25000000,
    "description": "Beautiful apartment with sea view and modern amenities",
    "latitude": 6.5244,
    "longitude": 3.3792,
    "images": [
      "http://localhost:3000/uploads/1750081234567-image1.jpg"
    ],
    "documents": [
      "http://localhost:3000/uploads/1750081234567-doc1.pdf"
    ]
  }
}
```

---

## 💬 Chat System Endpoints

### 5. Get Chat Messages
**Method**: `GET`  
**URL**: `{{base_url}}/api/chat`

**Headers**: None required

**Expected Response**:
```json
[
  {
    "text": "Mary Taiwo needs an apartment in Akobo",
    "timestamp": "2025-06-16T13:30:23.801Z"
  }
]
```

### 6. Send Chat Message
**Method**: `POST`  
**URL**: `{{base_url}}/api/chat`

**Headers**:
```
Content-Type: application/json
```

**Body** (raw JSON):
```json
{
  "text": "I have a perfect 2-bedroom apartment in Akobo area"
}
```

**Expected Response**:
```json
{
  "text": "I have a perfect 2-bedroom apartment in Akobo area",
  "timestamp": "2025-06-16T14:30:23.801Z"
}
```

---

## 🎯 Step-by-Step Testing Workflow

### Phase 1: Basic Setup (2 minutes)
1. **Start your server**: `npm start`
2. **Test server is running**: GET `{{base_url}}/api/listings`
3. **Verify empty state**: Should return `[]`

### Phase 2: Authentication (2 minutes)
1. **Register new user**: POST `/api/register`
2. **Login with existing user**: POST `/api/login`
3. **Test with invalid credentials**: Should return error

### Phase 3: Property Management (3 minutes)
1. **Get empty listings**: GET `/api/listings`
2. **Create listing without files**: POST `/api/listings` (text only)
3. **Create listing with files**: POST `/api/listings` (with images/documents)
4. **Verify listing created**: GET `/api/listings` again

### Phase 4: Chat System (1 minute)
1. **Get existing messages**: GET `/api/chat`
2. **Send new message**: POST `/api/chat`
3. **Verify message added**: GET `/api/chat` again

---

## 📁 File Upload Testing

### Preparing Test Files
1. **Create test images**: Save some JPG/PNG files
2. **Create test documents**: Save some PDF/DOC files
3. **Keep files small**: Under 5MB each

### Upload Process in Postman
1. Select **"Body"** tab
2. Choose **"form-data"**
3. Add your text fields (title, location, etc.)
4. For file fields:
   - Click the **key field** (images, documents)
   - Select **"File"** from dropdown
   - Click **"Select Files"** and choose your files

### Example File Upload Request
```
Key: title
Value: Modern Apartment

Key: location  
Value: Victoria Island

Key: price
Value: 35000000

Key: images
Type: File
Value: [Select apartment1.jpg, apartment2.jpg]

Key: documents
Type: File  
Value: [Select floorplan.pdf, contract.pdf]
```

---

## 🔍 Testing Error Cases

### 1. Invalid Registration
```json
{
  "email": "invalid-email",
  "password": "123",
  "userType": "invalid"
}
```
**Expected**: 400 Bad Request

### 2. Duplicate Email Registration
```json
{
  "email": "omotosomarytaiwo@gmail.com",
  "password": "password123",
  "userType": "agent"
}
```
**Expected**: 400 Bad Request - "Email already registered"

### 3. Invalid Login
```json
{
  "email": "nonexistent@email.com",
  "password": "wrongpassword"
}
```
**Expected**: 401 Unauthorized

### 4. Missing Required Fields
```json
{
  "title": "Apartment",
  "location": "Lagos"
  // Missing price, latitude, longitude
}
```
**Expected**: 400 Bad Request

---

## 📊 Response Status Codes

| Status | Meaning | Example |
|--------|---------|---------|
| 200 | Success | GET requests |
| 201 | Created | POST requests |
| 400 | Bad Request | Missing fields, invalid data |
| 401 | Unauthorized | Invalid login credentials |
| 500 | Server Error | Internal server issues |

---

## 🎥 Demo Tips for Postman

### Visual Setup
- **Use Collections**: Organize requests in folders
- **Save Responses**: Right-click → "Save Response"
- **Use Environment Variables**: For dynamic values
- **Add Descriptions**: Document each request

### Demo Flow
1. **Show empty state** (GET listings)
2. **Register new user** (POST register)
3. **Login existing user** (POST login)
4. **Create listing** (POST listings with files)
5. **Show created listing** (GET listings)
6. **Send chat message** (POST chat)
7. **Show chat history** (GET chat)

### Key Moments to Highlight
- ✅ Successful file uploads
- ✅ Data persistence
- ✅ Error handling
- ✅ Security features
- ✅ Real-time updates

---

## 🛠️ Troubleshooting

### Common Issues
1. **Server not running**: Check `npm start` output
2. **CORS errors**: Verify server is running on correct port
3. **File upload fails**: Check file size and format
4. **JSON parsing errors**: Verify Content-Type headers

### Debug Steps
1. Check server console for errors
2. Verify request URL and method
3. Check request headers and body
4. Test with curl commands as backup

---

**Now you're ready to test your Housing Agent Backend API with Postman! Start with the basic endpoints and work your way up to file uploads.** 🚀 