# Basic Chat Application

[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)
[![Node.js](https://img.shields.io/badge/Node.js-v14+-green.svg)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-v4+-blue.svg)](https://www.mongodb.com/)

A real-time group chat application built with modern web technologies, enabling seamless communication between multiple users in private chat rooms.

## Features

- Real-time messaging with WebSocket
- Secure user authentication
- Persistent chat history
- Responsive web interface
- Group chat functionality

## Tech Stack

- **Backend**: Node.js, Express.js
- **Real-time Communication**: Socket.IO
- **Database**: MongoDB
- **Template Engine**: EJS

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- npm

### Installation

```bash
git clone https://github.com/ZBS-1910/Basic-ChatApp.git
cd Basic-chat-app
npm install
```

Create a `.env` file in the root directory:
```
MONGODB_URI=your_mongodb_connection_string
PORT=3000
```

### Running the Application

```bash
npm run dev
```
Open your browser and navigate to `http://localhost:3000`

## API Overview

- **GET `/chat/:roomid/:user`**: Get chat interface and previous messages.
- **POST `/group`**: Create a new group chat.
- **WebSocket Events**: `join_room`, `new_msg`, `msg_rcvd`.

## Project Structure

```
Basic-chat-app/
├── config/
├── models/
├── views/
├── index.js
├── .env
├── package.json
└── package-lock.json
```

## License

This project is licensed under the ISC License.
