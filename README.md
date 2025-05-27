# hangman-
Hangman Game
Hangman is a word-guessing game where one player (computer) thinks of a word, and the other player tries to guess it by suggesting letters. Each incorrect guess results in a part of a hangman being drawn( life deducted) the player is provided with finite number of lives, and the game ends when either the word is guessed correctly or when the player runs out of lives.
#code:
import random

# List of words
word_list = ["python", "programming", "hangman", "developer", "keyboard"]
chosen_word = random.choice(word_list)
word_length = len(chosen_word)
lives = 6

# Display with underscores
display = ["_" for _ in range(word_length)]

print("Welcome to Hangman!")
print(display)
# Game loop
while "_" in display and lives > 0:
    guess = input("Guess a letter: ").lower()

    if guess in display:
        print(f"You've already guessed '{guess}'.")

    # Check if guess is in the word
    if guess in chosen_word:
        for i in range(word_length):
            if chosen_word[i] == guess:
                display[i] = guess
        print(f"Good guess: {' '.join(display)}")
    else:
        lives -= 1
        print(f"Wrong guess. You lost a life. Lives left: {lives}")
        print("Current word:", " ".join(display))

# End result
if "_" not in display:
    print("🎉 You win! The word was:", chosen_word)
    print("lives left:", lives )
else:
    print("😢 You lose. The word was:", chosen_word)
