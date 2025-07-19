# Hangman-game
import random

def hangman():
    word_list = ["python", "hangman", "programming", "chatgpt", "computer"]
    word = random.choice(word_list)
    guessed = "_" * len(word)
    guessed_correctly = list(guessed)
    guessed_letters = []
    attempts = 6

    print("Welcome to Hangman!")
    print("Guess the word:")
    print(" ".join(guessed_correctly))

    while attempts > 0 and "_" in guessed_correctly:
        guess = input("Enter a letter: ").lower()

        if not guess.isalpha() or len(guess) != 1:
            print("Please enter a single alphabet.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess in word:
            print("Good guess!")
            for i in range(len(word)):
                if word[i] == guess:
                    guessed_correctly[i] = guess
        else:
            attempts -= 1
            print(f"Wrong guess. Attempts left: {attempts}")

        print(" ".join(guessed_correctly))
        print("Guessed letters:", ", ".join(guessed_letters))

    if "_" not in guessed_correctly:
        print("🎉 Congratulations! You won!")
    else:
        print(f"💀 You lost! The word was: {word}")

# Run the game
hangman()
