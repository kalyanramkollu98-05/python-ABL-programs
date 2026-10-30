# 1. Problem Statement
Develop a Python program to generate a retail store bill for multiple products. The program should accept product names, quantities, prices, and categories. It should calculate the total amount, apply category-specific taxes, provide discounts based on purchase thresholds, and enforce a maximum discount limit. Finally, it should generate an itemized invoice showing the subtotal, discount, tax amount, and grand total.
# 2. Algorithm
1. Start the program.
2. Read the number of products.
3. Enter product name, category, quantity, and unit price.
4. Calculate the amount for each product.
5. Calculate subtotal of all products.
6. Apply category-specific tax rates:
   - Grocery – 5%
   - Personal Care – 18%
   - Other – 12%
7. Calculate discount based on subtotal:
   - Subtotal ≥ ₹500: 5% discount.
   - Subtotal ≥ ₹1000: 10% discount.
8. Apply maximum concession limit of ₹1000.
9. Calculate total tax.
10. Calculate grand total.
11. Display the itemized invoice.
12. Stop.
# 3. Flowchart (Mermaid)
   ```mermaid
   
flowchart TD
    A([Start]) --> B[/Enter number of products/]
    B --> C[/Enter product name, category, quantity and price/]
    C --> D[Calculate product amount]
    D --> E{More products?}
    E -->|Yes| C
    E -->|No| F[Calculate subtotal and category taxes]
    F --> G{Subtotal >= 1000?}
    G -->|Yes| H[Apply 10% discount]
    G -->|No| I{Subtotal >= 500?}
    I -->|Yes| J[Apply 5% discount]
    I -->|No| K[No discount]
    H --> L[Apply maximum concession limit]
    J --> L
    K --> L
    L --> M[Calculate grand total]
    M --> N[/Display itemized invoice/]
    N --> O([Stop])
```
# 4. Source Code (Python)

print("===== RETAIL BILLING SYSTEM =====")

n = int(input("Enter number of products: "))

subtotal = 0
total_tax = 0

products = []

for i in range(n):
    print("\nProduct", i + 1)

    name = input("Enter product name: ")
    category = input("Enter category (grocery/personal care/other): ").lower()
    quantity = int(input("Enter quantity: "))
    price = float(input("Enter unit price: "))

    amount = quantity * price

    if category == "grocery":
        tax_rate = 5
    elif category == "personal care":
        tax_rate = 18
    else:
        tax_rate = 12

    tax = amount * tax_rate / 100

    subtotal += amount
    total_tax += tax

    products.append(
        (name, quantity, price, amount, tax_rate)
    )
# 5. Sample Input
Enter number of products: 3

Product 1
Enter product name: Rice
Enter category: grocery
Enter quantity: 2
Enter unit price: 120

Product 2
Enter product name: Soap
Enter category: personal care
Enter quantity: 3
Enter unit price: 40

Product 3
Enter product name: Oil
Enter category: other
Enter quantity: 2
Enter unit price: 180

# Calculate discount
if subtotal >= 1000:
    discount = subtotal * 0.10
elif subtotal >= 500:
    discount = subtotal * 0.05
else:
    discount = 0

# Maximum concession limit
discount = min(discount, 1000)

grand_total = subtotal - discount + total_tax

# Display invoice
print("\n========== ITEMIZED INVOICE ==========")
print("Product   Qty   Price   Amount   Tax")

for p in products:
    print(f"{p[0]:10} {p[1]:3} {p[2]:7.2f} "
          f"{p[3]:8.2f} {p[4]}%")

print("--------------------------------------")
print("Subtotal       : Rs.", round(subtotal, 2))
print("Discount       : Rs.", round(discount, 2))
print("Total Tax      : Rs.", round(total_tax, 2))
print("Grand Total    : Rs.", round(grand_total, 2))
print("======================================")
5. Sample Input
Enter number of products: 3

Product 1
Enter product name: Rice
Enter category: grocery
Enter quantity: 2
Enter unit price: 120

Product 2
Enter product name: Soap
Enter category: personal care
Enter quantity: 3
Enter unit price: 40

Product 3
Enter product name: Oil
Enter category: other
Enter quantity: 2
Enter unit price: 180
# 6. Sample Output
========== ITEMIZED INVOICE ==========

Product   Qty   Price   Amount   Tax
Rice        2   120.00   240.00   5%
Soap        3    40.00   120.00  18%
Oil         2   180.00   360.00  12%

--------------------------------------
Subtotal       : Rs. 720.00
Discount       : Rs. 36.00
Total Tax      : Rs. 76.80
Grand Total    : Rs. 760.80
======================================
7. Screenshot
<img width="1529" height="860" alt="image" src="https://github.com/user-attachments/assets/9f1c6a40-f700-43d7-8d4e-17316be51b8b" />

