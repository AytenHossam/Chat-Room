# Chat-Room 

A fully functional chat room application built in Java that allows multiple users to communicate in real time over the same local network (LAN). The system supports multiple concurrent users through threading and sockets, includes a MySQL database for storing messages and user data, and follows a clean MVC architecture for both client and server.

---

## Project Overview

This chat system consists of two main components:

- **Client Application**: Each user runs a Java-based UI client that connects to the chat server, sends/receives messages, and optionally saves chat logs locally.
- **Server Application**: Handles all message broadcasting, user management, and database operations. Supports multiple clients using Java threading.

---

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

---

## Technologies Used

- Java SE
- Java Sockets
- Multi-threading
- MySQL (via JDBC)
- MVC Architecture
- JavaFX (if GUI is included)
- Object Serialization (for message transport)

---

## Project Structure

chat-server/
├── clientSide/ # All client-side code
│ ├── Controllers/ # GUI logic (if GUI is used)
│ ├── DAO/ # DB access from client (optional)
│ ├── Database/ # DB connection logic
│ ├── Model/ # Client-side data models
│ ├── Threads/ # Listener threads for incoming messages
│ └── View/ # UI layouts (FXML or terminal-based)
├── serverSide/ # All server-side code
│ ├── Controllers/ # Server-side processing logic
│ ├── DAO/ # Database logic
│ ├── Database/ # DB connection and setup
│ ├── Model/ # Server-side models
│ └── Threads/ # Handles each client connection
├── Common/ # Shared model classes
│ └── Model/
└── Main.java # Entry point to start server or client

yaml
Copy
Edit

---

## How It Works

1. **Server Initialization**  
   Run `Main.java` to start the server. It listens on a specified port and creates a thread for every connected client.

2. **Client Connection**  
   Clients connect by running their `Main.java`, entering their name and server IP. Messages are serialized and sent via sockets.

3. **Database Storage**  
   All messages are saved into a MySQL table with timestamps and usernames.

4. **Local Chat Logs**  
   Each client can save chat history to their device as a `.txt` file.

---

## Setup Instructions

### Prerequisites
- Java JDK 11+
- MySQL Server
- IDE (IntelliJ, Eclipse) or terminal

### Database Setup

🛠️ Database Setup
1. Create the Database
sql
Copy
Edit
CREATE DATABASE chatroom;
2. Create the messages Table
sql
Copy
Edit
USE chatroom;

CREATE TABLE messages (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(100),
    message TEXT,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
3. Update Database Credentials
Update your database connection settings in the following files:

clientSide/Database/Connection.java

serverSide/Database/Connection.java

▶️ Compile & Run
1. Compile All Java Files
bash
Copy
Edit
javac Main.java
Or use your IDE (like IntelliJ or Eclipse) to build the project.

2. Run the Server
bash
Copy
Edit
java Main
(Make sure the server IP and port are correctly configured)

3. Run the Client(s)
From any device on the same Wi-Fi:

bash
Copy
Edit
java Main
Enter your username and the server IP when prompted.

✅ Example Use Case
Start the server on one machine (e.g., 192.168.1.10)

Start the client on another device connected to the same LAN

Enter a username and server IP to join the room

Start messaging with other connected users

Messages are stored in MySQL and optionally saved locally
GitHub: @AytenHossam

