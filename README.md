[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-8d59dc4de5201274e310e4c54b9627a8934c3b88527886e3b421487c677d23eb.svg)](https://classroom.github.com/a/-EgJTiFp)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=10600753&assignment_repo_type=AssignmentRepo)
items_data = [
   {
      "itemId": 0,
      "itemName": "Crunch",
      'itemPrice': 9,
   },{
      "itemId": 1,
      "itemName": "M&M's",
      'itemPrice': 4,
   },{
      "itemId": 2,
      "itemName": "Snickers",
      'itemPrice': 4,
   },{
      "itemId": 3,
      "itemName": "Takis",
      'itemPrice': 8,
   },{
      "itemId": 4,
      "itemName": "San Pellegrino",
      'itemPrice': 5,
   },
]
item = []
reciept = """
\t\tPRODUCT NAME -- COST
"""
sum = 0
run = True

print("------- Vending Machine Program with Python-------\n\n")
print("----------The Items In Stock Are----------\n\n")


for i in items_data:
   print(
      f"Item: {i['itemName']} --- Price: {i['itemPrice']} --- Item ID: {i['itemId']}")


def vendingMachine(items_data, run, item):
   while run:
      buyItem = int(
         input("\n\nEnter the item code for the item you want to buy: "))
      if buyItem < len(items_data):
         item.append(items_data[buyItem])
      else:
         print("THE PRODUCT ID IS WRONG!")
      moreItems = str(
         input("type any key to add more things, and type q to stop:  "))
      if moreItems == "q":
         run = False
   receiptValue = int(
      input(("1. Print the bill? 2. Only print the total sum: ")))
   if receiptValue == 1:
      print(createReceipt(item, reciept))
   elif receiptValue == 2:
      print(sumItem(item))
   else:
      print("INVALID")


def sumItem(item):
   sumItems = 0
   for i in item:
      sumItems += i["itemPrice"]
   return sumItems


def createReceipt(item, reciept):
   for i in item:
      reciept += f"""
      \t{i["itemName"]} -- {i['itemPrice']}
      """
   reciept += f"""
      \tTotal --- {sumItem(item)}
      """
   return reciept


# Main Code
vendingMachine(items_data, run, item)
