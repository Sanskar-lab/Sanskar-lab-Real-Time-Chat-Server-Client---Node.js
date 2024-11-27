# Real-Time Chat Application Using Sockets

# Overview
This project implements a simple chat application where clients can connect to a server using sockets and exchange messages in real-time. The server supports multiple client connections and broadcasts messages to all clients, excluding the sender. The client has a text-based interface to send and receive messages in a shared chatroom environment.

# Project Structure
The project is divided into two main components:

Server: The server listens for incoming connections, accepts clients, and broadcasts messages to all clients.


Client: A simple command-line interface (CLI) application that connects to the server, sends messages, and receives messages in real-time.


# Technologies Used

Node.js: JavaScript runtime used to implement both the server and client.

TCP/IP Sockets: For network communication between the server and clients.

Threading/Asynchronous I/O: To handle multiple clients concurrently.

# Instructions to Run the Application

Prerequisites

Install Node.js (version 16.x or higher) on your machine. You can download it from here.
Make sure your firewall allows incoming and outgoing connections on the port that the server listens to (default is 3000).

# Steps to Run the Server

# Setup .env file
PORT=...

MONGO_DB_URI=...

JWT_SECRET=...

NODE_ENV=...


#  Build the app

npm run build

# Start the app
npm start

# Architecture and Concurrency Handling

Server Architecture

The server is designed to listen for incoming TCP socket connections.

It handles multiple client connections concurrently using Node.js’s asynchronous event-driven model (non-blocking I/O) rather than multi-threading. This ensures efficient handling of multiple clients without performance bottlenecks.

The server uses a global clients array to keep track of connected clients. When a message is received from one client, it is broadcasted to all other clients.


Client Architecture

Each client runs in its own instance, connecting to the server over a socket.

The client reads messages from the server asynchronously and displays them in real-time on the console.

The client’s interface allows users to send messages to the server by typing text and pressing Enter.


Concurrency Handling

The server uses Node.js's built-in event loop to handle multiple clients concurrently. This avoids blocking operations when waiting for network responses.

The client interacts with the server in a non-blocking fashion, sending and receiving messages asynchronously.


# Assumptions and Design Choices

No external libraries: As per the requirements, the application uses only the Node.js built-in libraries (net for TCP communication and readline for user input) to avoid external dependencies.

Broadcasting messages: The server broadcasts all messages to every client except the sender. This creates a simple chatroom where all participants see each other's messages.

Command-line interface: We opted for a text-based interface for simplicity and to meet the project requirements. A graphical interface could be added for future enhancements.
Error Handling and Robustness

The server checks for disconnections and gracefully removes clients from the list of active connections when they disconnect.

Client disconnections are detected, and the server stops broadcasting to a disconnected client.
Both client and server are protected against basic network errors (e.g., connection failure, invalid inputs).

# Future Enhancements
Private Messaging: Implement functionality to send private messages between users.

User Authentication: Add a simple authentication system where users can log in with a username.

Graphical Interface: Build a GUI using a framework like Electron.js or React for a more user-friendly experience.
