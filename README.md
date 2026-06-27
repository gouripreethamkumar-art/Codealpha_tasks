1)import random

# List of predefined words
words = ["apple", "mango", "tiger", "house", "table"]

# Select a random word
word = random.choice(words)

guessed = ""
wrong = 0
limit = 6

print("Welcome to Hangman Game!")

while wrong < limit:
    display = ""

    # Display guessed letters
    for letter in word:
        if letter in guessed:
            display += letter + " "
        else:
            display += "_ "

    print("\nWord:", display)

    # Check if word is completed
    if "_" not in display:
        print("🎉 Congratulations! You guessed the word:", word)
        break

    guess = input("Enter a letter: ").lower()

    if guess in guessed:
        print("You already guessed that letter.")
        continue

    guessed += guess

    if guess not in word:
        wrong += 1
        print("Wrong guess!")
        print("Remaining chances:", limit - wrong)

if wrong == limit:
    print("\nGame Over!")
    print("The word was:", word)

  2)# Hardcoded stock prices
stocks = {
    "AAPL": 180,
    "TSLA": 250,
    "MSFT": 350,
    "GOOGL": 140,
    "AMZN": 130
}

total = 0

# Open file
file = open("portfolio.txt", "w")

n = int(input("Enter number of stocks: "))

file.write("Stock Portfolio\n")
file.write("-------------------------\n")

for i in range(n):
    name = input("Enter stock name: ").upper()

    if name in stocks:
        quantity = int(input("Enter quantity: "))

        investment = stocks[name] * quantity
        total += investment

        print(name, "=", investment)

        file.write(name + " Quantity: " + str(quantity) +
                   " Price: $" + str(stocks[name]) +
                   " Investment: $" + str(investment) + "\n")
    else:
        print("Stock not available.")
        file.write(name + " - Stock not available\n")

print("\nTotal Investment Value = $", total)

file.write("\nTotal Investment Value = $" + str(total))
file.close()

print("Data saved in portfolio.txt")
