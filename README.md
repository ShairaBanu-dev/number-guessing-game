# number-guessing-game
### **Backend Spring Boot - Number Guessing Game Application**

#### **Project Overview**

The **Number Guessing Game** backend is a Spring Boot application that allows users to play a number guessing game. Users can register, log in, and start a game where they attempt to guess a randomly generated number between 1 and 10. The backend provides the logic for user authentication, game management, and tracking scores. It uses **Spring Boot** as the main framework, **Spring Security** for authentication, and **JPA** for database management.



#### **Key Features**

1. **User Registration & Login**:
   - **User Registration**: Users can create a new account by providing a unique username and password. The password is securely hashed using **Spring Security’s PasswordEncoder** before storing it in the database.
   - **User Login**: After registering, users can log in by providing their credentials. The backend authenticates users by comparing the hashed password stored in the database with the one entered.

2. **Game Management**:
   - **Start Game**: Users can start a new game, where the system generates a random target number between 1 and 10. The number of attempts made by the user is tracked.
   - **Guessing Mechanism**: Users input guesses, and the backend provides feedback:
     - **Too High** or **Too Low** if the guess is incorrect.
     - **Correct Guess** when the user guesses the correct number.
   - **Game Over**: The game ends when the user guesses the correct number, and the number of attempts is recorded. The backend stores the best score for each user (the least number of attempts to guess the correct number).

3. **Leaderboard**:
   - The backend tracks the **top scores** for the number of attempts taken by each user to guess the number. The application retrieves the **top 10 best scores** from the database and displays them to the users.

4. **Database Interaction**:
   - The backend utilizes **JPA** with **Spring Data** for database management. It uses two main entities:
     - **User**: Stores user information (username and password).
     - **Game**: Stores game-specific information such as the target number, attempts, and best score.
   - The application ensures that users can only have one active game at a time.



#### **Technologies Used**

- **Spring Boot**: A robust, easy-to-use framework for building backend applications quickly.
- **Spring Security**: For handling user authentication and securely storing passwords.
- **Spring Data JPA**: For interacting with the database using JPA repositories.
- **H2 Database**: An in-memory database for development and testing purposes (can be swapped for any production database like MySQL or PostgreSQL).
- **Java**: The core programming language used to develop the backend logic.


#### **API Endpoints**

1. **POST /auth/register**:
   - Registers a new user by accepting a `username` and `password` in the request body.
   - **Response**: Returns a message indicating whether registration was successful or if the username already exists.

2. **POST /auth/login**:
   - Authenticates the user by checking the provided `username` and `password`.
   - **Response**: Returns a message indicating whether the login was successful or if the credentials are incorrect.

3. **POST /game/start**:
   - Starts a new game for the authenticated user.
   - **Response**: Returns a message with instructions and a random number for the user to guess.

4. **POST /game/guess**:
   - Accepts a `guessedNumber` and provides feedback on whether the guess was too high, too low, or correct.
   - **Response**: Returns feedback based on the guessed number and the status of the game.

5. **GET /game/top-scores**:
   - Retrieves the top 10 scores (the least number of attempts) from all users.
   - **Response**: Returns a list of top scores.



#### **Security**

- **Password Hashing**: All passwords are securely hashed using **BCrypt** before storing them in the database.
- **Authentication**: User login is handled by comparing the input password with the hashed password stored in the database.
- **JWT (optional)**: For session management, a **JWT (JSON Web Token)** can be used to securely authenticate and authorize users for subsequent API calls.

#### **How It Works:**

1. The user registers by sending a `POST` request to `/auth/register`.
2. The user logs in by sending a `POST` request to `/auth/login`.
3. The user starts a new game by sending a `POST` request to `/game/start`.
4. The user makes guesses by sending a `POST` request to `/game/guess` with the guessed number.
5. The user can check the top scores with a `GET` request to `/game/top-scores`.


