# 1. Problem Statement
Managing a college canteen manually can lead to billing errors, incorrect stock records, and difficulties in handling multiple customer orders.

The Smart Canteen Order and Stock Management system is designed to process successive customer orders, calculate bills automatically, update available inventory, reject orders when requested quantities are unavailable, and generate a daily sales summary.

Objectives:
1. Display available food items, prices, and stock quantities.
2. Process multiple customer orders successively.
3. Calculate individual customer bills.
4. Automatically update inventory after successful orders.
5. Reject unavailable items or quantities.
6. Calculate total daily sales.
7. Display item-wise sales and remaining stock.
# 2. Algorithm
1. Start the program.
2. Initialize the canteen menu with item names, prices, and stock quantities.
3. Initialize total daily sales to zero.
4. Enter the number of customer orders.
5. For each customer:
   - Enter customer name.
   - Enter the number of different items requested.
6. For every requested item:
   - Read item name and quantity.
   - Check whether the item exists.
   - Check whether the requested quantity is valid.
   - Check whether sufficient stock is available.
7. If stock is available:
   - Calculate item cost.
   - Add the cost to the customer's bill.
   - Reduce the available stock.
   - Update item-wise sales.
8. Otherwise, reject the requested quantity and display a message.
9. Display the customer's final bill.
10. Repeat until all customer orders are processed.
11. Calculate total daily sales.
12. Display total orders, item-wise sales, and remaining stock.
13. Stop.
# 3. Flowchart (Mermaid)
   ```mermaid
   
flowchart TD
    A([Start]) --> B[Initialize Menu, Prices and Stock]
    B --> C[Initialize Daily Sales = 0]
    C --> D[/Enter Number of Orders/]
    D --> E[/Enter Customer Name and Items/]
    E --> F[/Enter Item Name and Quantity/]
    F --> G{Item Available?}
    G -->|No| H[Reject Item]
    G -->|Yes| I{Quantity Valid and Stock Sufficient?}
    I -->|No| H
    I -->|Yes| J[Calculate Item Cost]
    J --> K[Update Stock and Customer Bill]
    K --> L[Update Daily Sales]
    H --> M{More Items?}
    L --> M
    M -->|Yes| F
    M -->|No| N[Display Customer Bill]
    N --> O{More Customers?}
    O -->|Yes| E
    O -->|No| P[Display Daily Sales and Remaining Stock]
    P --> Q([Stop])
```
# 4. Source Code (Python)

def main():
    # Item: [Price, Available Stock]
    inventory = {
        "idli": [30, 40],
        "dosa": [50, 30],
        "tea": [15, 50],
        "sandwich": [60, 20]
    }

    daily_sales = 0
    completed_orders = 0

    units_sold = {
        item: 0 for item in inventory
    }

    print("=" * 55)
    print("SMART CANTEEN ORDER AND STOCK MANAGEMENT")
    print("=" * 55)

    print("\nAVAILABLE MENU")

    for item, details in inventory.items():
        print(f"{item.title():<15} "
              f"Price: INR {details[0]} "
              f"Stock: {details[1]}")

    total_orders = int(input("\nEnter number of customer orders: "))

    if total_orders < 0:
        print("Invalid number of orders.")
        return

    for order in range(1, total_orders + 1):

        customer = input(
            f"\nEnter customer name for order {order}: "
        )

        item_count = int(input("Enter number of different items: "))

        bill = 0

        print(f"\nOrder for {customer}")

        for i in range(item_count):

            item = input("Enter item name: ").lower().strip()
            quantity = int(input("Enter quantity: "))

            if item not in inventory:
                print("Rejected: Item not available.")
                continue

            if quantity <= 0:
                print("Rejected: Invalid quantity.")
                continue

            price, stock = inventory[item]

            if quantity > stock:
                print(f"Rejected: Only {stock} "
                      f"{item}(s) available.")
                continue

            amount = price * quantity

            # Update stock and sales
            inventory[item][1] -= quantity
            units_sold[item] += quantity

            bill += amount

            print(f"Accepted: {quantity} x "
                  f"{item.title()} = INR {amount:.2f}")

        daily_sales += bill

        if bill > 0:
            completed_orders += 1

        print(f"Bill for {customer}: INR {bill:.2f}")

    print("\n" + "=" * 55)
    print("DAILY SALES SUMMARY")
    print("=" * 55)

    print(f"Total customer orders: {total_orders}")
    print(f"Orders with sales: {completed_orders}")
    print(f"Total daily sales: INR {daily_sales:.2f}")

    print("\nITEM-WISE SALES AND REMAINING STOCK")

    print(f"{'Item':<15}{'Units Sold':>12}{'Stock Left':>14}")
    print("-" * 41)

    for item, details in inventory.items():
        print(f"{item.title():<15}"
              f"{units_sold[item]:>12}"
              f"{details[1]:>14}")

    print("=" * 55)


if __name__ == "__main__":
    main()
# 5. Sample Input
od item	Price (₹)	Stock
Idli	30	40
Dosa	50	30
Tea	15	50
Sandwich	60	20

Customer orders:
Customer	Item	Quantity
Anu	Dosa	2
Anu	Tea	3
Ravi	Idli	5
Ravi	Sandwich	25

The sandwich request is rejected because only 20 sandwiches are available.
# 6. Sample Output
=======================================================
SMART CANTEEN ORDER AND STOCK MANAGEMENT
=======================================================

AVAILABLE MENU

Idli       Price: INR 30   Stock: 40
Dosa       Price: INR 50   Stock: 30
Tea        Price: INR 15   Stock: 50
Sandwich   Price: INR 60   Stock: 20

Enter number of customer orders: 2

Enter customer name for order 1: Anu
Enter number of different items: 2

Order for Anu

Enter item name: dosa
Enter quantity: 2
Accepted: 2 x Dosa = INR 100.00

Enter item name: tea
Enter quantity: 3
Accepted: 3 x Tea = INR 45.00

Bill for Anu: INR 145.00

Enter customer name for order 2: Ravi
Enter number of different items: 2

Order for Ravi

Enter item name: idli
Enter quantity: 5
Accepted: 5 x Idli = INR 150.00

Enter item name: sandwich
Enter quantity: 25
Rejected: Only 20 sandwich(s) available.

Bill for Ravi: INR 150.00
# 7. Daily Sales Summary
=======================================================
                 DAILY SALES SUMMARY
=======================================================

Total customer orders: 2
Orders with sales: 2
Total daily sales: INR 295.00

ITEM-WISE SALES AND REMAINING STOCK

Item             Units Sold    Stock Left
-----------------------------------------
Idli                    5             35
Dosa                    2             28
Tea                     3             47
Sandwich                0             20

=======================================================
# 8. Program Screenshot
<img width="1250" height="1425" alt="image" src="https://github.com/user-attachments/assets/45bef97f-8f32-4f5c-a8a5-51ca8f6c6038" />

