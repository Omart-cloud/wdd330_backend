# Housing Agent Backend - 4-Minute Demo Script

## 🎯 Demo Overview
**Application**: Housing Agent Backend API  
**Duration**: 4 minutes  
**Target Audience**: Technical stakeholders, developers, or potential clients  
**Goal**: Showcase a complete real estate platform backend with user authentication, property listings, and chat functionality

---

## 📋 Pre-Demo Setup Checklist

### Technical Setup
- [ ] Start the server: `npm start` or `npm run dev`
- [ ] Ensure server is running on `http://localhost:3000`
- [ ] Have Postman, Insomnia, or similar API testing tool ready
- [ ] Prepare sample images and documents for upload testing
- [ ] Clear browser cache if testing frontend integration

### Data Preparation
- [ ] Note existing users in the system (3 users already registered)
- [ ] Prepare sample property listing data
- [ ] Have chat messages ready to demonstrate

---

## 🎬 Demo Script (4 Minutes)

### **Introduction (30 seconds)**
*"Hello everyone! Today I'm excited to demonstrate the Housing Agent Backend - a comprehensive real estate platform API that connects property agents with clients. This backend provides secure user authentication, property listing management, file uploads, and real-time chat functionality."*

### **1. Architecture Overview (45 seconds)**
*"Let me start by showing you the tech stack and architecture..."*

**Show:**
- Package.json (Express.js, bcrypt, multer, cors)
- Server.js structure
- API endpoints overview

**Key Points:**
- Node.js/Express.js backend
- JSON file-based data storage
- RESTful API design
- File upload handling with Multer
- Secure password hashing with bcrypt

### **2. User Authentication System (60 seconds)**
*"The platform supports two types of users - agents and clients, with secure authentication..."*

**Demonstrate:**
1. **Registration** - Show POST `/api/register`
   ```json
   {
     "email": "demo@example.com",
     "password": "securepass123",
     "userType": "agent"
   }
   ```

2. **Login** - Show POST `/api/login`
   ```json
   {
     "email": "omotosomarytaiwo@gmail.com",
     "password": "password123"
   }
   ```

**Key Features:**
- Password hashing with bcrypt
- User type differentiation (agent/client)
- Email validation
- Secure session management

### **3. Property Listing Management (90 seconds)**
*"The core feature is the property listing system that allows agents to upload properties with images and documents..."*

**Demonstrate:**
1. **Get All Listings** - GET `/api/listings`
   - Show current empty state
   - Explain the structure

2. **Create New Listing** - POST `/api/listings`
   ```json
   {
     "title": "Modern 3-Bedroom Apartment",
     "location": "Lekki, Lagos",
     "price": 25000000,
     "description": "Beautiful apartment with sea view",
     "latitude": 6.5244,
     "longitude": 3.3792
   }
   ```
   - Upload multiple images (up to 5)
   - Upload documents (up to 3)
   - Show file storage in uploads folder

3. **Show Created Listing** - GET `/api/listings` again
   - Display the new listing with image URLs
   - Show file paths and structure

**Key Features:**
- Multi-file upload support
- Geographic coordinates for mapping
- Structured property data
- File serving capabilities

### **4. Chat System (45 seconds)**
*"The platform includes a real-time chat system for communication between agents and clients..."*

**Demonstrate:**
1. **Get Chat Messages** - GET `/api/chat`
   - Show existing message: "Mary Taiwo needs an apartment in Akobo"

2. **Send New Message** - POST `/api/chat`
   ```json
   {
     "text": "I have a perfect 2-bedroom apartment in Akobo area"
   }
   ```

3. **Show Updated Chat** - GET `/api/chat` again
   - Display conversation flow

**Key Features:**
- Real-time message storage
- Timestamp tracking
- Simple but effective communication

### **5. Data Persistence & Security (30 seconds)**
*"All data is persistently stored and secured..."*

**Show:**
- JSON files: users.json, listings.json, chat.json
- File uploads directory structure
- Password hashing demonstration
- CORS configuration for frontend integration

### **Conclusion (30 seconds)**
*"This Housing Agent Backend provides a solid foundation for a real estate platform. It handles user authentication, property management, file uploads, and communication - all essential features for connecting agents and clients. The API is ready for frontend integration and can be easily extended with additional features like search, filtering, and notifications."*

---

## 🎥 Recording Tips

### Visual Setup
- **Screen Recording**: Use OBS Studio, Camtasia, or Loom
- **Resolution**: 1920x1080 or higher
- **Frame Rate**: 30fps for smooth playback
- **Audio**: Clear microphone, quiet environment

### Recording Flow
1. **Start with code overview** (30s)
2. **Switch to API testing tool** (3m)
3. **End with file system view** (30s)

### Key Moments to Highlight
- ✅ Successful API responses
- ✅ File uploads working
- ✅ Data persistence
- ✅ Error handling
- ✅ Security features

### Pacing Guidelines
- **Introduction**: 30 seconds
- **Architecture**: 45 seconds  
- **Authentication**: 60 seconds
- **Listings**: 90 seconds
- **Chat**: 45 seconds
- **Security**: 30 seconds
- **Conclusion**: 30 seconds

---

## 🛠️ Troubleshooting Guide

### Common Issues
1. **Server won't start**: Check if port 3000 is available
2. **File upload fails**: Ensure uploads directory exists
3. **CORS errors**: Verify frontend origin is allowed
4. **JSON parsing errors**: Check data format in requests

### Backup Plan
- Have screenshots ready of key features
- Prepare sample responses for offline demo
- Keep a list of all API endpoints handy

---

## 📊 Demo Success Metrics

### What to Demonstrate
- ✅ All API endpoints working
- ✅ File upload functionality
- ✅ User authentication flow
- ✅ Data persistence
- ✅ Error handling
- ✅ Security features

### Questions to Be Ready For
- "How scalable is this solution?"
- "What about database integration?"
- "How do you handle real-time features?"
- "What's the deployment strategy?"

---

## 🎯 Post-Demo Actions

### Follow-up Materials
- API documentation
- Deployment guide
- Frontend integration examples
- Database migration plan

### Next Steps
- Frontend development
- Database integration (MongoDB/PostgreSQL)
- Real-time features (WebSocket)
- Mobile app development
- Production deployment

---

**Good luck with your demo! Remember to speak clearly, demonstrate confidently, and highlight the value your application brings to the real estate industry.** 🚀 