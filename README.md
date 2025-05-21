# Basic Chat Application

[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)
[![Node.js](https://img.shields.io/badge/Node.js-v14+-green.svg)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-v4+-blue.svg)](https://www.mongodb.com/)

A real-time group chat application built with modern web technologies, enabling seamless communication between multiple users in private chat rooms.

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
  - [Running the Application](#running-the-application)
- [Quick Start Guide](#quick-start-guide)
- [API Documentation](#api-documentation)
  - [RESTful Endpoints](#restful-endpoints)
  - [WebSocket Events](#websocket-events)
  - [Error Handling](#error-handling)
- [Usage](#usage)
  - [Browser Interface](#browser-interface)
  - [Testing Guide](#testing-guide)
- [Security Features](#security-features)
- [Performance Tips](#performance-tips)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [Version History](#version-history)
- [License](#license)

## Features

- Real-time messaging with WebSocket
- Secure user authentication
- Persistent chat history
- Responsive web interface
- Group chat functionality
- Automatic message synchronization
- Message persistence across sessions

## Tech Stack

- **Backend**: Node.js, Express.js
- **Real-time Communication**: Socket.IO
- **Database**: MongoDB
- **Template Engine**: EJS
- **Environment Management**: dotenv
- **Development Tools**: nodemon

## Getting Started

### Prerequisites

Ensure you have the following installed:

- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- npm (comes with Node.js)

### Installation

1. Clone the repository:
```bash
git remote add origin https://github.com/ZBS-1910/Basic-ChatApp.git
```
2. Install dependencies:
```bash
cd Basic-chat-app
npm install
```

3. Set up environment variables:
Create a `.env` file in the root directory with the following variables:
```
MONGODB_URI=your_mongodb_connection_string
eg:- MONGODB_URI=mongodb://localhost:27017/
PORT=3000
```

### Running the Application

1. Start the development server:
```bash
npm run dev
```

2. Open your browser and navigate to `http://localhost:3000`

## Quick Start Guide

1. **Create a Family Group**
```bash
curl -X POST http://localhost:3000/group \
  -H "Content-Type: application/json" \
  -d '{"name": "Family Group", "description": "Main family chat"}'
```

2. **Join the Chat Room**
```javascript
// In your browser console
const socket = io('http://localhost:3000');
socket.emit('join_room', { roomid: 'family-chat-123' });
```

3. **Send Your First Message**
```javascript
socket.emit('new_msg', {
  roomid: 'family-chat-123',
  sender: 'sanket',
  message: 'Hi everyone!'
});
```

## Security Features

1. **Authentication**
   - Secure password hashing
   - Session-based authentication
   - Protection against unauthorized access

2. **Data Security**
   - Encrypted MongoDB connection
   - Protected WebSocket connections
   - Secure cookie handling

3. **Rate Limiting**
   - Prevents spam messages
   - Limits concurrent connections
   - Protects against brute force attacks

## Performance Tips

1. **Optimal Usage**
   - Keep WebSocket connections alive
   - Use efficient message sizes
   - Implement proper error handling

2. **Best Practices**
   - Use meaningful room IDs
   - Implement proper message validation
   - Handle connection errors gracefully

## Troubleshooting

### Common Issues

1. **Messages Not Appearing**
   - Check WebSocket connection
   - Verify room ID is correct
   - Ensure user is logged in

2. **Login Issues**
   - Verify MongoDB connection
   - Check environment variables
   - Clear browser cache

3. **Performance Problems**
   - Monitor server resources
   - Check for memory leaks
   - Optimize MongoDB queries

## Version History

- **v1.0.0** (2025-05-21)
  - Initial release
  - Real-time chat functionality
  - Group chat support
  - Basic authentication

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Guidelines

1. Follow the existing code style
2. Add tests for new features
3. Update documentation
4. Maintain backward compatibility
5. Include clear commit messages

## API Documentation

### RESTful Endpoints

#### Chat Room Endpoints

1. **GET `/chat/:roomid/:user`**
   - Retrieves chat interface with room information and previous messages
   - Parameters:
     - `roomid`: Chat room identifier
     - `user`: Current user's username
   - Response:
     ```json
     {
       "roomid": "family-chat-123",
       "user": "sanket",
       "groupname": "Family Group",
       "previousmsgs": [
         {
           "sender": "mom",
           "content": "Dinner is ready! Come join us."
         },
         {
           "sender": "dad",
           "content": "Sanket, don't forget your project meeting tomorrow."
         },
         {
           "sender": "brother",
           "content": "Hey bro, want to play cricket after dinner?"
         }
       ]
     }
     ```

2. **GET `/group`**
   - Retrieves group creation interface
   - Response: HTML template for group creation

3. **POST `/group`**
   - Creates a new group chat
   - Request Body:
     ```json
     {
       "name": "Family Group",
       "description": "Family chat for daily updates and plans"
     }
     ```
   - Response: Redirects to chat interface

### WebSocket Events

1. **`join_room`**
   - Join a specific chat room
   - Data:
     ```json
     {
       "roomid": "family-chat-123"
     }
     ```

2. **`new_msg`**
   - Send a new message to a room
   - Data:
     ```json
     {
       "roomid": "family-chat-123",
       "sender": "sanket",
       "message": "I'll be home in 15 minutes. See you all!"
     }
     ```

3. **`msg_rcvd`**
   - Event triggered when a new message is received
   - Data:
     ```json
     {
       "roomid": "family-chat-123",
       "sender": "mom",
       "message": "Great! I'll keep dinner warm."
     }
     ```

### Real-life Usage Examples

#### Family Chat
1. **Creating a Family Group**
```json
{
  "name": "Family Group",
  "description": "Main family chat for daily updates"
}
```

2. **Sending Family Updates**
```json
{
  "roomid": "family-chat-123",
  "sender": "mom",
  "message": "Reminder: Doctor's appointment tomorrow at 3 PM"
}
```

#### Friends Chat
1. **Creating a Friends Group**
```json
{
  "name": "College Friends",
  "description": "Group for college reunion planning"
}
```

2. **Sending Group Messages**
```json
{
  "roomid": "friends-chat-456",
  "sender": "sanket",
  "message": "Let's meet this weekend for a movie night!"
}
```

#### Work Group
1. **Creating a Work Group**
```json
{
  "name": "Project Team",
  "description": "Team chat for project updates"
}
```

2. **Sending Work Updates**
```json
{
  "roomid": "work-chat-789",
  "sender": "team-lead",
  "message": "Today's meeting at 10 AM - Discussing sprint planning"
}
```

## Usage

### Browser Interface

1. **Authentication**
   - Register a new account
   - Login with existing credentials
   - Secure session management

2. **Chat Features**
   - Create new group chats
   - Join existing rooms
   - Send and receive messages
   - View message history
   - Real-time user presence

### Testing Guide

1. **Basic Chat Functionality**
   - Create multiple user accounts
   - Send messages between users
   - Verify real-time message delivery
   - Test message persistence

2. **Real-time Features**
   - Open multiple browser instances
   - Verify message synchronization
   - Test user presence indicators
   - Check connection handling

3. **Error Handling**
   - Test invalid inputs
   - Verify error messages
   - Test edge cases
   - Check security features

### API Testing

1. **Using cURL**
```bash
# Create a group
curl -X POST http://localhost:3000/group \
  -H "Content-Type: application/json" \
  -d '{"name": "Test Group", "description": "For testing"}'

# Join a room
const socket = io('http://localhost:3000');
socket.emit('join_room', { roomid: 'test-room-123' });
```

## Project Structure

```
Basic-chat-app/
├── config/          # Configuration files
├── models/          # MongoDB models
├── views/           # EJS templates
├── index.js         # Main application file
├── .env             # Environment variables
├── package.json     # Project dependencies
└── package-lock.json
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the ISC License - see the LICENSE file for details.

## Acknowledgments

- Socket.IO for real-time communication
- Express.js for the web framework
- MongoDB for data persistence
- All contributors who have helped improve this project# Basic-ChatApp
# Basic-ChatApp
