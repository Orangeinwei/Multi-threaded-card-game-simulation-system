# Card Game Simulation

**Abstract**

The project is dedicated to generating a multi-threaded application that shall be a multi-threaded card game simulation of a card game system that is scalable, thread-safe and supports concurrent player operations, and shall also be able to generate log files to validate game results. The game shall be able to perform the functions of a player drawing, discarding, evaluating their hands and declaring that they have four cards of the same number of points and winning the game.

**Directory**

- `src/` contains two folders: game development and testing. Each folder contains the corresponding development and testing code.
- After running the program, each user and deck log will be saved in the project's folder. Each log records the current and historical status of the corresponding player or deck.

**Prerequisites**

Before running the project or tests, ensure you have the following installed:

- Java Development Kit (JDK): Version 23.0.2 or higher.
- JUnit4: The testing framework used for the test suite.

**Project Structure**

*Development Module:*

These classes form the core of the CardGameApp project. They handle the game logic, player actions, and deck management.

- `Card.java`: Represents a single playing card with a non-negative integer face value.
- `Deck.java`: Models a deck of cards in the game. There are as many decks as there are players, and they are arranged in a ring topology.
- `GameStatus.java`: Serves as a shared communication mechanism to indicate when the game is over and which player (if any) won.
- `Player.java`: Represents a player in the game. Each player runs on its own thread and is responsible for managing its hand of cards, interacting with two decks (drawing and discarding), and logging its actions.
- `CardGame.java`: Acts as the entry point of the application. It reads user input, sets up the game (distributes cards to players and decks), starts player threads, and finally writes out the decks’ contents once the game concludes.

*Test Module:*

These classes test the functionality of the core game logic. They ensure that the game behaves as expected under various conditions.

- `CardTest.java`: Tests the functionality of the `Card` class. Verifies that cards are created with the correct values and that the `toString` method returns the expected string representation.
- `DeckTest.java`: Tests the functionality of the `Deck` class. Verifies that cards can be added to and drawn from the deck, and that the deck's contents are correct. Ensures that the deck behaves correctly when empty or when multiple cards are present.
- `PlayerTest.java`: Tests the functionality of the `Player` class. Verifies that players can draw and discard cards correctly, and that they can detect when they have a winning hand. Ensures that players prioritize discarding non-preferred cards.
- `GameStatusTest.java`: Tests the functionality of the `GameStatus` class. Verifies that the game state is correctly tracked and that only one player can declare victory. Ensures that subsequent victory declarations are ignored after the first one.
- `CardGameTest.java`: Tests the main game logic in the `CardGame` class. Verifies that the game initializes correctly, distributes cards as expected, and handles player threads properly. Ensures the game can detect the winner and terminate immediately.
- `GameFlowValidatorSorted.java`: A helper class for CardGameTest.java to validate the outputs.

**Installation / Setup:**

First, we need to open the folder in eclipse as following:
1. unzip cardsTests.zip
2. import it as a project in Eclipse

Second, run the 'CardGame' as the java application. The result and the details of the game we can clearly get from the output.

Third, If we would like to test out our game development code, we ought to make sure there is JUnit 4 installed in our eclipse. 
Here are installation steps of adding JUnit 4 library: 
1. Right click the file CardGameApp (the project's name). 
2. Choose the option 'Build Path' 
3. Click ' Add libaries' 
4. Click 'Next' 
5. Choose 'JUnit 4' 
6. Click 'Finish'

Then, right click any class in test.java package and run as JUnit 4. We will eventually get the testing result and outputs. We also offer the ' CardGameTestSuite' to test every part of main code in general.