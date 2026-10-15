
def check_password(password):
    score = 0
    feedback = []

    if len(password) >= 12:
        score += 1
    else:
        feedback.append("Use at least 12 characters.")

    if any(char.isupper() for char in password):
        score += 1
    else:
        feedback.append("Add an uppercase letter.")

    if any(char.islower() for char in password):
        score += 1
    else:
        feedback.append("Add a lowercase letter.")

    if any(char.isdigit() for char in password):
        score += 1
    else:
        feedback.append("Add a number.")

    if any(not char.isalnum() for char in password):
        score += 1
    else:
        feedback.append("Add a special character.")

    if score <= 2:
        strength = "Weak"
    elif score <= 4:
        strength = "Moderate"
    else:
        strength = "Strong"

    return strength, feedback


if __name__ == "__main__":
    password = input("Enter a test password: ")
    strength, feedback = check_password(password)

    print(f"\nPassword rating: {strength}")

    if feedback:
        print("\nSuggestions:")
        for item in feedback:
            print(f"- {item}")
    else:
        print("All basic checks passed!")
