import rando
import datetime
import os
import json

DATA_FILE = "quotes.json"

# Load quotes from file or create a default list
def load_quotes():
    if os.path.exists(DATA_FILE):
        with open(DATA_FILE, "r", encoding="utf-8") as f:
            return json.load(f)
    else:
        return [
            "Every day is a new beginning. Take advantage of it!",
            "Success is built with small but consistent steps.",
            "When you’re tired, learn to rest, not to quit.",
            "It’s never too late to become who you want to be.",
            "Believe you can, and you’re halfway there."
        ]

# Save quotes to fil
def save_quotes(quotes):
    with open(DATA_FILE, "w", encoding="utf-8") as f:
        json.dump(quotes, f, indent=4)

# Show a random quote
def show_random_quote(quotes):
    quote = random.choice(quotes)
    now = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    print(f"\n[{now}] Motivational Quote of the Day:\n{quote}\n")

# List all quotes
def list_quotes(quotes):
    print("\n--- All Quotes ---")
    for i, quote in enumerate(quotes, start=1):
        print(f"{i}. {quote}")
    print()

# Add a new quote
def add_quote(quotes):
    new_quote = input("\nEnter the new quote: ").strip()
    if new_quote:
        quotes.append(new_quote)
        save_quotes(quotes)
        print("✅ Quote added successfully!\n")
    else:
        print("⚠️ Empty quote not added.\n")

# Main menu
def main():
    quotes = load_quotes()
    
    while True:
        print("=== Motivational Quote Manager ===")
        print("1. Show random quote")
        print("2. List all quotes")
        print("3. Add a new quote")
        print("4. Exit")
        
        choice = input("Choose an option (1-4): ").strip()
        
        if choice == "1":
            show_random_quote(quotes)
        elif choice == "2":
            list_quotes(quotes)
        elif choice == "3":
            add_quote(quotes)
        elif choice == "4":
            print("Goodbye! Stay motivated! 💪")
            break
        else:
            print("Invalid choice, please try again.\n")

if __nam__ == "__main__":
    main()
