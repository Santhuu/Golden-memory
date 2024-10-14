# Golden-memory
import random
import string

def generate_password(length, include_uppercase=True, include_digits=True, include_symbols=True):
    # Define character sets
    lowercase = string.ascii_lowercase
    uppercase = string.ascii_uppercase if include_uppercase else ''
    digits = string.digits if include_digits else ''
    symbols = string.punctuation if include_symbols else ''
    
    # Create the character pool
    all_characters = lowercase + uppercase + digits + symbols
    
    if not all_characters:
        raise ValueError("At least one character set must be selected!")
    
    # Generate password
    password = ''.join(random.choice(all_characters) for _ in range(length))
    return password

def main():
    print("Welcome to the Random Password Generator!")
    
    # Get user preferences
    try:
        length = int(input("Enter the desired password length: "))
        if length <= 0:
            raise ValueError("Length must be a positive integer.")
        
        include_uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
        include_digits = input("Include digits? (y/n): ").lower() == 'y'
        include_symbols = input("Include symbols? (y/n): ").lower() == 'y'
        
        # Generate the password
        password = generate_password(length, include_uppercase, include_digits, include_symbols)
        print(f"\nYour generated password is: {password}\n")
    except ValueError as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    main()
