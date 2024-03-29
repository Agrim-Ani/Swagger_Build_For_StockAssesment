# Stock Price View Application(Backend Assesment Hypergrow.ai)

This repository contains the code for a Stock Price View Application that accesses and manages data from the Bombay Stock Exchange (BSE). The application is built using Node.js and Express.js, with MongoDB as the database.

## Project Structure

```plaintext
HYPERGROW_AI/
|-- config/
|   |-- dbConnection.js
|-- controllers/
|   |-- equityControllers.js
|   |-- favouriteController.js
|   |-- userController.js
|-- middleware/
|   |-- errorHandler.js
|   |-- validateTokenHandler.js
|-- models/
|   |-- equityModel.js
|   |-- favouriteModel.js
|   |-- userModel.js
|-- routes/
|   |-- equityRoutes.js
|   |-- favouriteRoutes.js
|   |-- userRoutes.js
|-- index.js
|-- script.js
```

## Installation and Setup

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd HYPERGROW_AI
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Set up the environment variables by creating a `.env` file in the root directory:

   ```plaintext
   PORT=<port-number>
   CONNECTION_STRING=<your-mongodb-connection-string>
   ACCESS_TOKEN_SECRET=<your-secret-key>
   ```

4. Run the script to populate the database with stock data:

   ```bash
   node script.js
   ```

5. Run the application:

   ```bash
   npm start
   ```

## API Usage

### Equity API

- **GET /api/stocks/top10**
  - Get the top 10 latest stocks.

    Example:
    ```plaintext
    GET /api/stocks/top10
    ```

- **GET /api/stocks?SC_NAME=<stock-name>**
  - Get a stock by name.

    Example:
    ```plaintext
    GET /api/stocks?SC_NAME=Reliance
    ```

- **GET /api/stocks/history?SC_NAME=<stock-name>**
  - Get stock price history list for UI graph.

    Example:
    ```plaintext
    GET /api/stocks/history?SC_NAME=TCS
    ```

### Favourites API

- **GET /api/fav**
  - Get all favourite stocks. (Requires user authentication)

    Example:
    ```plaintext
    GET /api/fav
    ```

- **POST /api/fav**
  - Add a stock to favourites. (Requires user authentication)

    Example:
    ```plaintext
    POST /api/fav
    Body: { "stockName": "Infosys" }
    ```

- **DELETE /api/fav/:id**
  - Remove a stock from favourites. (Requires user authentication)

    Example:
    ```plaintext
    DELETE /api/fav/608f19cfe3b07b001e1e3e23
    ```

### User API

- **POST /api/users/register**
  - Register a new user.

    Example:
    ```plaintext
    POST /api/users/register
    Body: { "username": "john_doe", "email": "john@example.com", "password": "password123" }
    ```

- **POST /api/users/login**
  - Login a user.

    Example:
    ```plaintext
    POST /api/users/login
    Body: { "email": "john@example.com", "password": "password123" }
    ```

- **GET /api/users/current**
  - Get current user information. (Requires user authentication)

    Example:
    ```plaintext
    GET /api/users/current
    ```

## Important Note

Before starting the server, make sure to run the `script.js` script to download the latest stock data from BSE(you can add date,month,year in the script to have stock data of your choice) and populate the database. This ensures that the application has the necessary stock documents for the APIs to function correctly.

**Note:** For /api/fav Routes Users must register and log in to perform actions such as adding, deleting, or retrieving favourite stocks. Authentication is required to access these routes for security purposes.
