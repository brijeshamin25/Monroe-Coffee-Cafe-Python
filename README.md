# Monroe-Coffee-Cafe-Python
import sys

#exception handeling for menu input
def MonCoffMen(que):
    response = None
    response = input(que)
    while response not in ("0"):
      print("Please enter number 0 to open Menu.")
      response = input(que)
    return response
menu = MonCoffMen('Enter "0" to open MENU : ')

#function with exception handeling with 3 paramaeters
def User(msg,t1,t2,t3):
    while True:
        try:
            coffee = (input(msg))
        except TypeError:
            print("Please Enter String Value!", t1, "OR", t2, "OR", t3)
            continue
        if coffee != t1 and coffee != t2 and coffee != t3:
            print("Please Enter proper option:", t1, "OR", t2, "OR", t3)
        else:
            return coffee

#function with exception handeling with 2 parameters         
def Value(val,n1,n2):
    while True:
        try:
            enter = input(val)
        except (ValueError, TypeError):
            print("Please enter proper option only",n1,n2)
            continue
        if enter != n1 and enter != n2:
            print("Enter only", n1, "or", n2)
        else:
            return enter

#function with exception handeling for quantity check
def Num(number,q1,q2):
    while True:
        try:
            quantity = int((input(number)))
        except (ValueError,TypeError):
            print("Please enter Number between 0 to ",sys.maxsize)
            continue
        if quantity < q1 or quantity > q2:
            print("Enter number between 0 to ",sys.maxsize)
        else:
            return quantity

#constant values
quaranta = 2.50
grosso = 1.75
lanky = 1.00

muffPrice = 3.00

salesTax = 6.25

#function for calculate salestax
def Sales():
    sTax = salesTax/100
    return sTax
salTax = Sales() 

#loop to continue program
while menu == "0":
    #menu for coffee type
    print("\n-----------MENU----------")
    print("What would you like to have in COFFEE Type :\n")
    print("1. dark brew")
    print("2. hazelnut")
    print("3. pumpkin spice")
    cstCoffee = User("Enter Coffee Type: ", "dark brew", "hazelnut", "pumpkin spice")
    
    #option for caffeine coffee
    print("\n----------Option----------")
    print("\n Please select coffee caffeine type :\n")
    print("1. regular")
    print("2. decaf")
    cofCaff = Value("You want Regular or Decaf coffee: ","regular","decaf")
    
    #options for coffee cream
    print("\n----------Option----------")
    print("\n Please select option with Milk or without Milk : \n")
    print("1. black coffee")
    print("2. milk")
    print("3. half and half")
    cofMilk = User("Ente kind of Coffee Milk: ","black coffee", "milk","half and half")

    #option for sugar in coffee
    print("\n----------Option----------")
    print("\n Please select sugar option : \n")
    print("1. sugar")
    print("2. no sugar")
    cofSug = Value("Enter Sugar option:", "sugar","no sugar")
    
    #Using function Num to check enter proper quantity
    qty = Num("\n Enter number of Coffee Quantity : ",1,sys.maxsize)
    
    #option for coffee and it's price
    print("\n----------Option----------")
    print("\n Please select option for differnt Coffee varient : \n")
    print("1. quaranta [ Cost => $", quaranta,"]")
    print("2. grosso [ cost => $", grosso,"]")
    print("3. lanky [ cost => $",lanky,"]")
    v1 = User("Select Coffee Varient : ", "quaranta", "grosso", "lanky")
    #calculate the total of quantity and coffee price
    if v1 == "quaranta":
        totalQty = qty * quaranta
    elif v1 == "grosso":
        totalQty = qty * grosso
    else:
        totalQty = qty * lanky
    
    def PriceCoffee():
        if v1 == "quaranta":
            price = 2.50
        elif v1 == "grosso":
            price = 1.75 
        else:
            price = 1.00
        return price
    prsCoff = PriceCoffee()

    
    #muffin option
    print("\n----------Muffins Option--------- ")
    print("\n Do you want Muffins? \n")
    print("1. yes")
    print("2. no")
    opt = Value("Do you want Muffins :","yes", "no")
    
    #muffin menu will open if enter yes
    if opt == "yes":
        #menu for muffins
        print("\n----------MENU----------")
        print("\n What kind of muffin do you wnat? \n")
        print("1. corn muffins")
        print("2. blueberry muffins")
        print("3. chocolate chip muffins")
        muff = User("What kind of muffin do you want:","corn muffins","blueberry muffins","chocolate chip muffins")
        
        #option for muffin toast
        print("\n----------Option----------")
        print("\n Do you want Muffins Toasted: \n")
        print("1. toasted")
        print("2. without toast")
        muffTost = Value("Do you want Toasted Muffins: ","toasted", "without toast")
        
        #option for muffin toppings
        print("\n----------Option----------")
        print("\n Select any Toppings for Muffins.\n")
        print("1. butter")
        print("2. margarine")
        print("3. orange marmalade")
        muffTopp = User("What Toppings do you want:","butter","margarine","orange marmalade")
            
        #Using function Num to check enter proper quantity
        muffQty = Num("\n Enter Muffins quantity :",1,sys.maxsize)
    else:
        #else if user enter no for muffins
        cstName = input("\n Enter Customer Name: ")
        tax = salTax * totalQty
        total = totalQty + tax
        
        print("\n\n ======================================= Receipt ======================================")
        
        print("\n*** Coffee ***")
        print("\n",v1,"(",cstCoffee,",",cofCaff,",",cofSug,",",cofMilk,")","\t" ,"Quantity: ",qty, "at $",prsCoff,"each")
        print("\n \t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t Sub Total: $",totalQty)
    
        print("\n*** Sales Tax ***")
        print("\n Tax: \t\t\t\t - \t\t\t\t",salesTax,"%","\t\t\t\t - \t\t\t\t\t $",format(tax,",.2f"))
        print("\n\n*** Toatl ***")
        print("\n Total Due: -------------------------------------------------------------------- $",format(total,",.2f"))
        print("\n Customer Name : ", cstName)
        
        print("\n\n\t\t\t\t===================================================")
        print("\n\n\t\t\t\t Thank You for Visiting the Monroe Coffee House!")
        print("\t\t\t\t\t\t\t\t Come Again Soon!")
        print("\n\n\t\t\t\t===================================================")
        
        menu = input("\n Enter any number to exit or enter 0 to continue.. : ")
        continue
    

    #execute this step if user enter yes for muffins
    muffTot = muffQty * muffPrice
    tax = (totalQty + muffTot) * salTax 
    total = totalQty + muffTot + tax    
    
    cstName = input("\n Enter Customer Name: ")
    
    print("\n\n ======================================= Receipt ======================================")
    
    print("\n*** Coffee ***")
    print("\n",v1,"(",cstCoffee,",",cofCaff,",",cofSug,",",cofMilk,")","\t" ,"Quantity: ",qty, "at $",prsCoff,"each")
    print("\n \t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t Sub Total: $",totalQty)
    
    print("\n\n*** Muffins ***")
    print("\n",muff," ","(",muffTost,",",muffTopp,")","\t","Quantity: ",muffQty,"at $",muffPrice,"each")
    print("\n \t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t Sub Total: $",muffTot)
    
    print("\n*** Sales Tax ***")
    print("\n Tax: \t\t\t\t - \t\t\t\t",salesTax,"%","\t\t\t\t - \t\t\t\t\t $",format(tax,",.2f"))
    
    print("\n\n*** Total ***")
    print("\n Total Due: -------------------------------------------------------------------- $",format(total,",.2f"))
    
    print("\n Customer Name : ", cstName)
    
    print("\n\n\t\t\t\t===================================================")
    print('\n\n\t\t\t\t Thank You for Visiting the Monroe Coffee House!')
    print("\t\t\t\t\t\t\t\t Come Again Soon!")
    print("\n\n\t\t\t\t===================================================")
    
    menu = input("\n Enter any number to exit or enter 0 to continue.. : ")
