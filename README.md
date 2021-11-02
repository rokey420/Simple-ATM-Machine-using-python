#CODE:
pinCode = ["1234", "1999", "2424"] 
accountHoldersName = ["abhinav", "rishitha", "tejesh"]
accountNumber = ['1353', '199281', "182838"]
balance = [567000, 21873, 2341871]
while True:
    print("Welcome To Simple ATM System")
    inputName = input("Enter Your Name: ")
    inputName = inputName.lower()
    inputPin = 0000 
    index = 0
    u = False
    count = 0 
    for name in accountHoldersName:
        if name == inputName:
            index = count
            inputPin = input("\nEnter Pin Number: ")
        count = count + 1       
    if inputPin == pinCode[index]:
        flag = True
    else:

        print("Invalid data.")
        continue
    if flag == True:
        print("\nYour account number is: ",accountNumber[index])
        print("Your account balance is: Rs.", balance[index])
        drawOrDeposit = input("\nDo you want to draw or deposit cash (draw/deposit/no): ")
        if drawOrDeposit == "draw":
            amount = input("\nEnter the amount you want to draw: ")
            amount = int(amount)
            if amount > balance[index]:
                print("insuffcient amount.")
                continue
            if(amount%100 == 0 or amount%500 == 0 or amount%2000 == 0):
                u = True
            else:
                print("Invalid data.")
                continue    
            if u == True:
                y = amount//2000
                u = amount-y*2000
                p = u//500
                g=u-p*500
                m=g//100
                finalamount = y*2000 + p*500 + m*100
                remainingBalalnce = balance[index] - finalamount 
                balance.remove(balance[index]) 
                balance.insert(index,remainingBalalnce)
                availableBalance = print("\nYour available balance is: ",remainingBalalnce)
                print("\n N.O Of 2000/- Notes = ",y)
                print("\n N.O Of 500/- Notes = ",p)
                print("\n N.O Of 100/- Notes = ",m)
                print("\nThank you for using this Simple ATM System.")
        if drawOrDeposit  == "deposite":
            amount = input("Enter the amount you want to deposit: ")        
            amount = int(amount)
            remainingBalalnce = balance[index] + amount #adding the deposited amount.
            balance.remove(balance[index])#removing the old ammount from the list and adding the new list after draw.
            balance.insert(index,remainingBalalnce)
            availableBalance = print("Your available balance is: ",remainingBalalnce)
            print("\n\nThank you for using this Simple ATM System.")           


