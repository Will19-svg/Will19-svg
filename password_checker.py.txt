import re

def check_password_strength(password):
    length_criteria = len(password) >= 8
    lowercase_criteria = bool(re.search(r'[a-z]', password))
    uppercase_criteria = bool(re.search(r'[A-Z]', password))
    number_criteria = bool(re.search(r'[0-9]', password))
    special_char_criteria = bool(re.search(r'[!@#$%^&*(),.?":{}|<>]', password))

    criteria_met = sum([length_criteria, lowercase_criteria, uppercase_criteria, number_criteria, special_char_criteria])

    if criteria_met == 5:
        strength = "Very Strong"
    elif criteria_met >= 3:
        strength = "Strong"
    elif criteria_met >= 2:
        strength = "Weak"
    else:
        strength = "Very Weak"
        
    return strength

password = input("Enter a password to check: ")
print(f"Password strength: {check_password_strength(password)}")
