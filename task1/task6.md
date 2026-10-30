# 1. Problem Statement
Develop a Python program to calculate the total manufacturing cost and profitability of a product. The program should accept material costs, labour charges, wastage percentage, machine costs, and selling price. It should calculate the total production cost, profit or loss, and profit percentage. Finally, the program should compare the actual profit with a specified profit target and identify whether the production meets the required target.
# 2. Algorithm
1. Start the program.
2. Enter the product name.
3. Enter the quantity of products manufactured.
4. Enter the material cost per unit.
5. Enter the labour charges per unit.
6. Enter the wastage percentage.
7. Enter the machine cost.
8. Enter the selling price per unit.
9. Enter the required profit target percentage.
10. Calculate total material cost.
11. Calculate labour cost.
12. Calculate wastage cost.
13. Calculate total manufacturing cost.
14. Calculate total selling amount.
15. Calculate profit or loss.
16. Calculate profit percentage.
17. Compare actual profit percentage with the target.
18. Display the manufacturing cost and profitability report.
19. Stop the program.
# 3. Flowchart (Mermaid)
   ```mermaid
   
flowchart TD
    A([Start]) --> B[/Enter product details/]
    B --> C[/Enter quantity, material cost, labour cost/]
    C --> D[/Enter wastage percentage and machine cost/]
    D --> E[/Enter selling price and profit target/]
    E --> F[Calculate material cost]
    F --> G[Calculate labour cost]
    G --> H[Calculate wastage cost]
    H --> I[Calculate total manufacturing cost]
    I --> J[Calculate total selling amount]
    J --> K[Calculate profit or loss]
    K --> L[Calculate profit percentage]
    L --> M{Profit percentage >= Target?}
    M -->|Yes| N[Production meets profit target]
    M -->|No| O[Production does not meet target]
    N --> P[/Display cost and profit report/]
    O --> P
    P --> Q([Stop])
```
# 4. Source Code (Python)

print("===== MANUFACTURING COST AND PROFITABILITY ANALYSIS =====")

product = input("Enter product name: ")

quantity = int(input("Enter production quantity: "))

material = float(input("Enter material cost per unit: "))

labour = float(input("Enter labour charges per unit: "))

wastage_percent = float(input("Enter wastage percentage: "))

machine = float(input("Enter total machine cost: "))

selling_price = float(input("Enter selling price per unit: "))

target = float(input("Enter profit target percentage: "))

# Calculate costs
material_cost = quantity * material

labour_cost = quantity * labour

wastage_cost = material_cost * wastage_percent / 100

total_cost = material_cost + labour_cost + wastage_cost + machine

# Calculate sales and profit
total_sales = quantity * selling_price

profit = total_sales - total_cost

if total_cost > 0:
    profit_percent = (profit / total_cost) * 100
else:
    profit_percent = 0

# Display report
print("\n===== MANUFACTURING REPORT =====")

print("Product Name       :", product)
print("Production Quantity:", quantity)
print("Material Cost      : Rs.", round(material_cost, 2))
print("Labour Cost        : Rs.", round(labour_cost, 2))
print("Wastage Cost       : Rs.", round(wastage_cost, 2))
print("Machine Cost       : Rs.", round(machine, 2))

print("----------------------------------")

print("Total Cost         : Rs.", round(total_cost, 2))
print("Total Sales        : Rs.", round(total_sales, 2))

if profit >= 0:
    print("Profit             : Rs.", round(profit, 2))
else:
    print("Loss               : Rs.", round(abs(profit), 2))

print("Profit Percentage  :", round(profit_percent, 2), "%")

print("----------------------------------")

if profit_percent >= target:
    print("Production meets the profit target.")
else:
    print("Production does not meet the profit target.")

print("==================================")
# 5. Sample Input
Enter product name: Chair
Enter production quantity: 100
Enter material cost per unit: 200
Enter labour charges per unit: 50
Enter wastage percentage: 10
Enter total machine cost: 2000
Enter selling price per unit: 350
Enter profit target percentage: 15
# 6. Sample Output
===== MANUFACTURING REPORT =====

Product Name       : Chair
Production Quantity: 100
Material Cost      : Rs. 20000.0
Labour Cost        : Rs. 5000.0
Wastage Cost       : Rs. 2000.0
Machine Cost       : Rs. 2000.0

----------------------------------
Total Cost         : Rs. 29000.0
Total Sales        : Rs. 35000.0
Profit             : Rs. 6000.0
Profit Percentage  : 20.69 %

----------------------------------
Production meets the profit target.
==================================
# 7. Screenshot
<img width="1448" height="1086" alt="image" src="https://github.com/user-attachments/assets/39f3d343-8d62-42aa-8183-90233c8171ac" />
