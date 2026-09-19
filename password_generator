import secrets

import string

print("--- MY PASSWORD GENERATOR ---")

while True:
    try:

        length = int(input("Enter password length (e.g., 8 or 12): "))
        if length < 4:
            print("Please choose a length of at least 4.")
            continue
        break

    except ValueError:

        print("That's not a valid number. Try again.")

letters = string.ascii_letters   # a-z and A-Z
digits = string.digits           # 0-9
symbols = string.punctuation     # @, #, $, etc.

all_characters = letters + digits + symbols

password_chars = [
    secrets.choice(letters),
    secrets.choice(digits),
    secrets.choice(symbols),
]
password_chars += [secrets.choice(all_characters) for _ in range(length - 3)]

secrets.SystemRandom().shuffle(password_chars)
password = "".join(password_chars)

print("\nYour secure password is:", password)

has_lower = any(c.islower() for c in password)
has_upper = any(c.isupper() for c in password)
has_digit = any(c.isdigit() for c in password)
has_symbol = any(c in symbols for c in password)
variety_score = sum([has_lower, has_upper, has_digit, has_symbol])

if length < 8 or variety_score < 2:
    print("Status: Weak Password! (Too short or too simple)")
elif length < 12 or variety_score < 3:
    print("Status: Medium Password. (Good for basic accounts)")
else:
    print("Status: Strong Password! (Very secure)")
