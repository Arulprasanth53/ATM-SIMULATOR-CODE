# ATM-SIMULATOR-CODE 
class ATM:
    def __init__(self, user_pin, initial_balance=0):
        self.pin = user_pin
        self.balance = initial_balance

    def authenticate(self, entered_pin):
        return entered_pin == self.pin

    def check_balance(self):
        print(f"Your current balance is ₹{self.balance}")

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"₹{amount} deposited successfully.")
        else:
            print("Invalid deposit amount.")

    def withdraw(self, amount):
        if 0 < amount <= self.balance:
            self.balance -= amount
            print(f"₹{amount} withdrawn successfully.")
        else:
            print("Insufficient funds or invalid amount.")

def main():
    atm = ATM(user_pin="1234", initial_balance=5000)
    print("Welcome to Python ATM 💳")

    entered_pin = input("Enter your PIN: ")
    if atm.authenticate(entered_pin):
        while True:
            print("\n1. Check Balance\n2. Deposit\n3. Withdraw\n4. Exit")
            choice = input("Choose an option: ")

            if choice == '1':
                atm.check_balance()
            elif choice == '2':
                amount = float(input("Enter deposit amount: ₹"))
                atm.deposit(amount)
            elif choice == '3':
                amount = float(input("Enter withdrawal amount: ₹"))
                atm.withdraw(amount)
            elif choice == '4':
                print("Thank you for using Python ATM. Goodbye!")
                break
            else:
                print("Invalid option. Please try again.")
    else:
        print("Authentication failed. Invalid PIN.")

if __name__ == "__main__":
    main()
