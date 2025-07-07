# Chat-Room 

A fully functional chat room application built in Java that allows multiple users to communicate in real time over the same local network (LAN). The system supports multiple concurrent users through threading and sockets, includes a MySQL database for storing messages and user data, and follows a clean MVC architecture for both client and server.

## Project Overview

This chat system consists of two main components:

- **Client Application**: Each user runs a Java-based UI client that connects to the chat server, sends/receives messages, and optionally saves chat logs locally.
- **Server Application**: Handles all message broadcasting, user management, and database operations. Supports multiple clients using Java threading.

## Features

- Real-time messaging over local Wi-Fi (LAN)
- Supports multiple simultaneous clients
- Threaded server for handling concurrent connections
- MySQL database integration for:
  - Message persistence
  - Chat logs
  - User data (if extended)
- MVC architecture with clear separation between model, view, and controller
- CRUD operations on messages
- Local saving of chat history by clients
- Modular structure with reusable DAO and utility classes
- Shared `Common` model between client and server

## Technologies Used

- Java SE
- Java Sockets
- Multi-threading
- MySQL (via JDBC)
- MVC Architecture
- JavaFX (if GUI is included)
- Object Serialization (for message transport)

## Folder Structure

```
chat-server/
├── clientSide/
│   ├── Controllers/
│   ├── DAO/
│   ├── Database/
│   ├── Model/
│   ├── Threads/
│   └── View/
├── serverSide/
│   ├── Controllers/
│   ├── DAO/
│   ├── Database/
│   ├── Model/
│   └── Threads/
├── Common/
│   └── Model/
└── Main.java
```

## Database Setup

### 1. Create the Database

```sql
CREATE DATABASE chatroom;
```

### 2. Create the `messages` Table

```sql
USE chatroom;

CREATE TABLE messages (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(100),
    message TEXT,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

### 3. Update Database Credentials

Update your database connection settings in the following files:

- `clientSide/Database/Connection.java`
- `serverSide/Database/Connection.java`

## Compile & Run

### 1. Compile All Java Files

```bash
javac Main.java
```

### 2. Run the Server

```bash
java Main
```

### 3. Run the Client(s)

```bash
java Main
```

## Example Use Case

- Start the server on one machine (e.g., `192.168.1.10`)
- Start the client on another device connected to the same LAN
- Enter a username and server IP to join the room
- Start messaging with other connected users
- Messages are stored in MySQL and optionally saved locally

## Author

Developed by Ayten Hossam  
GitHub: [@AytenHossam](https://github.com/AytenHossam)

## License

This project is licensed under the MIT License.
