{% include navigation.html %}

<h1>Data Structures Work</h1>
<h3><a href= "https://replit.com/@ReinhardtLotter/Menu?v=1">Replit Link</a></h3>

<iframe frameborder="0" width="100%" height="800px" src="https://replit.com/@ReinhardtLotter/Menu?lite=true#src/main.py">

<h2>Menu Code</h2>

```
    print("Fibonacci")
n1, n2 = 0, 1
count = 0
print("Fibonacci sequence:")
while count < 20:
   print(n1)
   sum = n1 + n2
   n1 = n2
   n2 = sum
   count += 1
 ```
    
```
    InfoDb = []
# List with dictionary records placed in a list  
InfoDb.append({  
               "FirstName": "Reinhardt",  
               "LastName": "Lotter",  
               "DOB": ["April 19"],  
               "Favorite_Animal": ["Lion","Dolphin"],  
               "Favorite_Colors":["Pink","Purple"]  
              })  

InfoDb.append({  
               "FirstName": "Christoff",  
               "LastName": "Lotter",  
               "DOB": ["October 24"],  
               "Favorite_Animal":["Shark","Zebra"],   
               "Favorite_Colors":["Green"] 
              })  

# given an index this will print InfoDb content
def print_data(n):
    print(InfoDb[n]["FirstName"], InfoDb[n]["LastName"])  # using comma puts space between values
    print("\t", "Favorite_Animal: ", end="")  # \t is a tab indent, end="" make sure no return occurs
    print(", ".join(InfoDb[n]["Favorite_Animal"]))  # join allows printing a string list with separator
    print()

# Hack 2: InfoDB loops. Print values from the lists using three different ways: for, while, recursion

  # hack 2a: def for_loop()
# for loop iterates on length of InfoDb
def for_loop():
  for n in range(len(InfoDb)):
      print_data(n)

    
  # hack 2b: def while_loop(0)
# while loop contains an initial n and an index incrementing statement (n += 1)
def while_loop(n):
  while n < len(InfoDb):
      print_data(n)
      n += 1
  return

  # hack 2c : def recursive_loop(0)
# recursion simulates loop incrementing on each call (n + 1) until exit condition is met
def recursive_loop(n):
  if n < len(InfoDb):
      print_data(n)
      recursive_loop(n + 1)
  return # exit condition

def InfoDb_loops():
  print()
  print("For loop:")
  for_loop()
  print("While loop:")
  while_loop(0)  # requires initial index to start while
  print("Recursive loop:")
  recursive_loop(0)  # requires initial index to start recursion
 ```
    
```
# menuy.py - function style menu
# Imports typically listed at top
# each import enables us to use logic that has been abstracted to other files and folders
import Animation

# Main list of [Prompts, Actions]
# Two styles are supported to execute abstracted logic
# 1. file names will be run by exec(open("filename.py").read())
# 2. function references will be executed directly file.function()
main_menu = [
    ["Swap", "swap.py"],
    ["Matrix", "matrix.py"], 
    ["Christmas Tree", "christmastree.py"],
    ["Animation", Animation.ship],
]

# Submenu list of [Prompt, Action]
# Works similarly to main_menu
sub_menu = [
    ["Factors", None],
    ["GCD", None],
    ["LCM", None],
    ["Primes", None],
]

random_sub_menu = [
    ["Random1", None],
    ["Random2", None],
    ["Random3", None],
]

# Menu banner is typically defined by menu owner
border = "=" * 25
banner = f"\n{border}\nPlease Select An Option\n{border}"


# def menu
# using main_menu list:
# 1. main menu and submenu reference are created [Prompts, Actions]
# 2. menu_list is sent as parameter to menuy.menu function that has logic for menu control
def menu():
    title = "Function Menu" + banner
    menu_list = main_menu.copy()
    buildMenu(title, menu_list)

# def submenu
# using sub menu list above:
# sub_menu works similarly to menu()
def submenu():
    title = "Function Submenu" + banner
    buildMenu(title, sub_menu)
def Random_submenu():
    title = "Function Submenu" + banner
    buildMenu(title, random_sub_menu)

def buildMenu(banner, options):
    # header for menu
    print(banner)
    # build a dictionary from options
    prompts = {0: ["Exit", None]}
    for op in options:
        index = len(prompts)
        prompts[index] = op

    # print menu or dictionary
    for key, value in prompts.items():
        print(key, '->', value[0])

    # get user choice
    choice = input("Type your choice> ")

    # validate choice and run
    # execute selection
    # convert to number
    try:
        choice = int(choice)
        if choice == 0:
            # stop
            return
        try:
            # try as function
            action = prompts.get(choice)[1]
            action()
        except TypeError:
            try:  # try as playground style
                exec(open(action).read())
            except FileNotFoundError:
                print(f"File not found!: {action}")
            # end function try
        # end prompts try
    except ValueError:
        # not a number error
        print(f"Not a number: {choice}")
    except UnboundLocalError:
        # traps all other errors
        print(f"Invalid choice: {choice}")
    except TypeError:
        print(f"Not callable {action}")
    # end validation try

    buildMenu(banner, options)  # recursion, start menu over again


if __name__ == "__main__":
    menu()
```    

<h2>Matrix Code </h2>

```
print("Matrix")
#matrix
matrix = [(1,2,3),(4,5,6),(7,8,9), (" ",0," ")]
for x in matrix:
    for y in x:
        print(y, end = " ")
    print()
```

<h2>Swap Code</h2>

```
print("Swap")
ageOne = 21
ageTwo = 16

print(ageOne,ageTwo)

def swapAge (ageOne, ageTwo):
    storAge = ageOne
    ageOne = ageTwo
    ageTwo = storAge
    return ageOne, ageTwo
  
age1,age2 = swapAge(ageOne, ageTwo)

print(age1,age2)
```

<h2>Christmas Tree Code</h2>

```
print("Christmas Tree")
#tree
tree = [("        ","*"," "),
        ("       ","* *"," "),
        ("      ","* * *"," "),
        ("     ","* * * *"," "),
        ("    ","* * * * *"," "),
        ("   ","* * * * * *"," "),
        ("  ","* * * * * * *"," "),
        (" ","* * * * * * * *"," "),
        ("","* * * * * * * * *"," "),
        ("       ","***"," "),
        ("       ","***"," "),
        ("       ","***"," "),
  ]
for x in tree:
    for y in x:
        print(y, end = " ")
    print()
```

<h2>Animation Code</h2>

```
import time

# terminal print commands
ANSI_CLEAR_SCREEN = u"\u001B[2J"
ANSI_HOME_CURSOR = u"\u001B[0;0H\u001B[2"
OCEAN_COLOR = u""
SHIP_COLOR = u"\u001B[32m\u001B[2D"
RESET_COLOR = u"\u001B[0m\u001B[2D"

def ocean_print():
    # print ocean
    print(ANSI_CLEAR_SCREEN, ANSI_HOME_CURSOR)
    print("\n\n\n\n")
    print(OCEAN_COLOR + "  " * 35)

# print ship with colors and leading spaces
def ship_print(position):
    print(ANSI_HOME_CURSOR)
    print(RESET_COLOR)
    sp = " " * position
    print(sp + "░░░░░░░░░░░░▄░░▄░▀█▄░░")
    print(sp + "░░▄████████▄██▄██▄██░░")
    print(sp + "░░█████████████▄████▌░")
    print(sp + "░░▌████████████▀▀▀▀▀░░")
    print(sp + "▒▀▒▐█▄▐█▄▐█▄▐█▄▒░▒░▒░▒")
    print(RESET_COLOR)

# ship function, iterface into this file
def ship():
  ocean_print()
  # loop control variables
  start = 0  # start at zero
  distance = 35  # how many times to repeat
  step = 1  # count by 2

  # loop purpose is to animate ship sailing
  for position in range(start, distance, step):
      ship_print(position)  # call to function with parameter
      time.sleep(.1)
 ```     
