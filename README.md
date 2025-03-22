# ChessApp Documentation

## Overview
ChessApp is a real-time multiplayer chess application built with Node.js, Socket.IO, and Chess.js. It enables two players to play chess while others can watch as spectators.

## Project Structure
```
ChessApp/
├── app.js                # Server application
├── public/
│   └── js/
│       └── chessgame.js  # Client-side game logic
├── views/
│   └── index.ejs        # Game interface template
└── README.md            # Documentation
```

## Setup and Installation

### Installation Steps
```bash
# Install dependencies
npm install express socket.io chess.js ejs

# Start the server
node app.js

# Access the application
open http://localhost:4000
```

## Server-Side Implementation (app.js)

### Core Components
- Express server setup
- Socket.IO integration
- Chess game state management
- Player role assignment

### Key Features
- Real-time move synchronization
- Player role management (white/black/spectator)
- Move validation
- Game state broadcasting

### Socket Events
| Event | Description |
|-------|-------------|
| `connection` | New player connects |
| `disconnect` | Player leaves |
| `move` | Player makes a move |
| `playerRole` | Assigns player color |
| `spectatorRole` | Assigns spectator status |
| `boardState` | Updates chess board state |
| `invalidMove` | Handles invalid moves |

## Client-Side Implementation (chessgame.js)

### Core Components
- Chess board rendering
- Drag-and-drop piece movement
- Socket event handling
- Board state management

### Key Functions

#### `renderBoard()`
- Renders the chess board UI
- Creates square elements
- Positions pieces
- Handles board orientation
- Sets up drag-and-drop events

#### `handleMove(source, target)`
- Processes piece movements
- Converts board coordinates to chess notation
- Emits move events to server

#### `getPieceUnicode(piece)`
- Maps chess pieces to Unicode characters
- Returns appropriate piece symbol

## Frontend Template (index.ejs)

### Features
- Responsive chess board layout
- CSS Grid-based board structure
- Piece styling and animations
- Board flipping for black player

### CSS Classes
| Class | Purpose |
|-------|---------|
| `.chessboard` | Main board container |
| `.square` | Individual board squares |
| `.piece` | Chess piece elements |
| `.flipped` | Rotated board for black player |
| `.light`/`.dark` | Square coloring |

## Technical Details

### Dependencies
```json
{
  "express": "^4.17.1",
  "socket.io": "^4.8.1",
  "chess.js": "^0.10.3",
  "ejs": "^3.1.6"
}
```

### Browser Support
- Modern browsers with ES6 support
- Drag-and-drop API support required

## Game Flow

### 1. Server Initialization
- Creates HTTP server
- Sets up Socket.IO
- Initializes chess game state

### 2. Player Connection
- First player gets white
- Second player gets black
- Additional players become spectators

### 3. Gameplay
- Players alternate turns
- Moves validated server-side
- Board updates broadcast to all clients

### 4. Move Processing
- Client initiates move
- Server validates
- All clients receive update

## Error Handling
- ✓ Invalid moves rejected
- ✓ Disconnection handling
- ✓ Turn enforcement
- ✓ Move validation