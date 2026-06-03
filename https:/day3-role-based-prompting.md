# Day 3 - Role Based Prompting

## Prompt Used:
Act as a senior Python developer with 10 years 
of experience. Write a simple function to add 
two numbers with proper comments.

## Claude's Response:

def add_two_numbers(num1, num2):
    """
    This function adds two numbers and returns the result.
    
    Parameters:
        num1 (int/float): First number
        num2 (int/float): Second number
    
    Returns:
        int/float: Sum of num1 and num2
    """
    
    # Add both numbers and store in result variable
    result = num1 + num2
    
    # Return the final result
    return result

# Taking input from user
first_number = float(input("Enter first number: "))
second_number = float(input("Enter second number: "))

# Calling the function
answer = add_two_numbers(first_number, second_number)

print(f"Sum of {first_number} and {second_number} is: {answer}")
