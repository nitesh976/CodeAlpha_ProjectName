# CodeAlpha_Hangman_Game

import random

words = ["python", "java", "coding", "program"]
chosen_word = random.choice(words)

display = []
for _ in chosen_word:
    display.append("_")

lives = 6
guessed_letters = []

while lives > 0 and "_" in display:
    print("\nCurrent word:", " ".join(display))
    guess = input("Guess a letter: ").lower()

    if guess in guessed_letters:
        print("Tum ye letter pehle hi guess kar chuke ho.")
        continue

    guessed_letters.append(guess)

    if guess in chosen_word:
        for index in range(len(chosen_word)):
            if chosen_word[index] == guess:
                display[index] = guess
        print("Correct guess!")
    else:
        lives -= 1
        print("Wrong guess! Lives left:", lives)

if "_" not in display:
    print("\nYou Win! 🎉 Word was:", chosen_word)
else:
    print("\nGame Over! ❌ Word was:", chosen_word)