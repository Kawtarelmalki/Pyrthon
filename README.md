# Pyrthon
 une calculatrice multifonction
 
import fractions
import math

# Function to solve proportions
def solve_proportion(a, b, x):
    return (b * x) / a

# Function to solve for x in equations
def solve_equation(a, b, c):
    return (c - b) / a

# Function to factor square roots
def factor_square_root(n):
    factors = []
    for i in range(2, int(math.sqrt(n)) + 1):
        while n % i == 0:
            factors.append(i)
            n //= i
    if n > 1:
        factors.append(n)
    return factors

# Function to convert decimals to fractions and percents
def convert_decimal(number):
    fraction = fractions.Fraction(number).limit_denominator()
    percent = number * 100
    return (fraction, percent)

# Function to convert fractions to decimals and percents
def convert_fraction(numerator, denominator):
    decimal = numerator / denominator
    percent = decimal * 100
    return (decimal, percent)

# Function to convert percents to decimals and fractions
def convert_percent(percent):
    decimal = percent / 100
    fraction = fractions.Fraction(percent).limit_denominator()
    return (decimal, fraction)

# Main function to handle user inputs and call the appropriate function
def main():
    while True:
        print("Select an operation:")
        print("1. Solve proportion")
        print("2. Solve equation for x")
        print("3. Factor square root")
        print("4. Convert decimal to fraction and percent")
        print("5. Convert fraction to decimal and percent")
        print("6. Convert percent to decimal and fraction")
        print("7. Quit")

        choice = input("Enter choice (1-7): ")

        if choice == '1':
            a = float(input("Enter first number: "))
            b = float(input("Enter second number: "))
            x = float(input("Enter third number: "))
            result = solve_proportion(a, b, x)
            print("Result: {}".format(result))

        elif choice == '2':
            a = float(input("Enter coefficient of x: "))
            b = float(input("Enter constant term: "))
            c = float(input("Enter value of equation: "))
            result = solve_equation(a, b, c)
            print("Result: {}".format(result))

        elif choice == '3':
            n = int(input("Enter number to factor: "))
            result = factor_square_root(n)
            print("Result: {}".format(result))

        elif choice == '4':
            number = float(input("Enter decimal number: "))
            fraction, percent = convert_decimal(number)
            print("Fraction: {0}, Percent: {1}%".format(fraction, percent))

        elif choice == '5':
            numerator = int(input("Enter numerator: "))
            denominator = int(input("Enter denominator: "))
            decimal, percent = convert_fraction(numerator, denominator)
            print("Decimal: {0}, Percent: {1}%".format(decimal, percent))

        elif choice == '6':
            percent = float(input("Enter percent: "))
            decimal, fraction = convert_percent(percent)
            print("Decimal: {0}, Fraction: {1}".format(decimal, fraction))

        elif choice == '7':
            break

        else:
            print("Invalid input")

if __name__ == '__main__':
    main()
