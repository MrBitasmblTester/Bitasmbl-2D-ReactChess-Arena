# Bitasmbl-2D-ReactChess-Arena

Develop a web-based 2D multiplayer chess game using React.js for the client, ASP.NET Core for the API, SignalR for real-time interactions, and PostgreSQL for durable game state storage.

## Tech Stack

- ASP.NET Core
- PostgreSQL
- React
- SignalR

## Requirements

- Real-time move broadcasting via SignalR hub
- Define EF Core entity for game persistence
- Implement basic client-side move validation

## Installation

bash
git clone https://github.com/your-org/Bitasmbl-2D-ReactChess-Arena.git
cd Bitasmbl-2D-ReactChess-Arena
# Server setup
cd Server
# Set environment variable for database connection
export ConnectionStrings__Default='Host=localhost;Database=reactchessdb;Username=postgres;Password=YourPassword'
# Apply migrations and start API
dotnet ef database update
dotnet run
# Client setup
cd ../Client
npm install
npm start


## Usage

Open http://localhost:3000 in your browser to create or join a chess game. Moves are validated client-side before being sent via SignalR, and all game state is stored in PostgreSQL.

## Implementation Steps

1. Initialize an ASP.NET Core Web API project for the server.
2. Add EF Core packages, define a Game entity and ChessDbContext.
3. Create and apply initial EF Core migration to PostgreSQL.
4. Implement a SignalR hub (ChessHub) to broadcast moves and listen for client events.
5. Scaffold the React client using Create React App.
6. Install @microsoft/signalr in the client and configure a HubConnection to ChessHub.
7. Build the chessboard component and incorporate basic client-side move validation logic.
8. Implement API controllers for creating new games and fetching existing game state.
9. Wire up SignalR events in React to send moves and update the UI in real time.
10. Test multiplayer gameplay locally across multiple browser windows.

## API Endpoints

- **POST /api/games**: Create a new chess game session.
- **GET /api/games/{gameId}**: Retrieve the current state of a game.
- **SignalR Hub (ChessHub)**: `/chesshub` endpoint handling real-time move messages and persisting them via EF Core.