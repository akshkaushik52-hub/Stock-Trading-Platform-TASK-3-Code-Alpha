# Java Stock Trading Platform

A beginner-friendly, console-based stock trading simulator built with Core Java and Object-Oriented Programming.

## Project Folder Structure

```text
TASK-3 , Stock Trading Platform/
├── README.md
├── src/
│   ├── MarketAsset.java
│   ├── Stock.java
│   ├── TransactionType.java
│   ├── Transaction.java
│   ├── Portfolio.java
│   ├── User.java
│   └── TradingPlatform.java
├── data/
│   ├── portfolio.csv
│   └── transactions.csv
└── out/
    └── compiled .class files
```

The `data` and `out` folders are created when you run and compile the project.

## How to Compile and Run

Open a terminal in the project folder and run:

```bash
javac -d out src/*.java
java -cp out TradingPlatform
```

## Main Features

- View predefined market stocks and prices.
- Buy shares using available balance.
- Sell owned shares with quantity validation.
- View current portfolio holdings.
- View complete transaction history.
- Generate a detailed portfolio report.
- Save and load portfolio and transaction data using CSV files.
- Uses `ArrayList` for transactions and `HashMap` for stocks and holdings.
- Includes exception handling and input validation.

## OOP Concepts Used

- **Encapsulation:** Class fields are private and accessed through public methods.
- **Abstraction:** `MarketAsset` is an abstract class with the abstract method `getDisplayInfo()`.
- **Inheritance:** `Stock` extends `MarketAsset`.
- **Polymorphism:** `TradingPlatform` displays `Stock` objects through `MarketAsset` references.

## Class-Wise Explanation

### `MarketAsset`

An abstract parent class for market items. It stores common fields such as stock symbol and name, and requires child classes to implement `getDisplayInfo()`.

### `Stock`

Represents a stock in the market. It stores the current stock price and validates that prices are always greater than zero.

Major methods:

- `getPrice()` returns the stock price.
- `setPrice()` updates and validates the price.
- `getDisplayInfo()` returns formatted stock details.

### `User`

Represents the person using the trading platform. Each user has a username and one `Portfolio`.

Major methods:

- `getUsername()` returns the username.
- `getPortfolio()` returns the user's portfolio.

### `Portfolio`

Stores available balance, owned stock quantities, and invested amounts. It handles buying, selling, value calculation, profit/loss calculation, and file storage.

Major methods:

- `buyStock()` buys shares after checking balance.
- `sellStock()` sells shares after checking owned quantity.
- `displayHoldings()` prints owned stocks.
- `calculateCurrentValue()` calculates current market value.
- `calculateProfitLoss()` compares market value with invested amount.
- `saveToFile()` and `loadFromFile()` handle portfolio CSV storage.

### `Transaction`

Represents one buy or sell operation. It stores transaction id, type, stock symbol, quantity, price, total amount, and date/time.

Major methods:

- `getTotalAmount()` returns quantity multiplied by price.
- `toCsv()` converts a transaction to a CSV row.
- `fromCsv()` creates a transaction from a saved CSV row.

### `TransactionType`

An enum with two values: `BUY` and `SELL`. It avoids using hard-coded strings for transaction types.

### `TradingPlatform`

The main menu-driven class. It creates predefined stocks, accepts user input, calls portfolio methods, records transactions, and saves/loads data.

Major methods:

- `start()` starts the application.
- `runMenu()` controls the menu loop.
- `viewAvailableStocks()` displays market stocks.
- `buyStock()` and `sellStock()` handle trading.
- `viewTransactionHistory()` prints all transactions.
- `generatePortfolioReport()` shows balance, holdings, value, and profit/loss.

## Sample Input/Output

```text
==============================================
       Welcome to Java Stock Trading App
==============================================
Enter your username: Ananya
No saved data found. Starting with a fresh account.

--------------- Main Menu ---------------
1. View available stocks
2. Buy stocks
3. Sell stocks
4. View portfolio holdings
5. View transaction history
6. Generate portfolio report
7. Save data
0. Exit
Choose an option: 1

Symbol   Company                  Price
------------------------------------------------
SBIN     State Bank of India      Rs.     780.30
TCS      Tata Consultancy         Rs.    3820.50
HDFC     HDFC Bank                Rs.    1675.80
WIPRO    Wipro Ltd                Rs.     510.40
RELI     Reliance Industries      Rs.    2910.75
INFY     Infosys Ltd              Rs.    1465.25

Choose an option: 2
Enter stock symbol to buy: TCS
Enter quantity to buy: 5
Purchase successful. Total cost: Rs. 19,102.50

Choose an option: 6

================ Portfolio Report ================
User: Ananya
Available balance: Rs. 80,897.50
Total invested amount: Rs. 19,102.50
Current portfolio value: Rs. 19,102.50
Profit/Loss: Rs. 0.00
Total account value: Rs. 100,000.00

Owned Stocks:
Symbol   Company                  Quantity   Avg Cost       Market Price   P/L
--------------------------------------------------------------------------------
TCS      Tata Consultancy         5          Rs. 3820.50    Rs. 3820.50    Rs. 0.00
==================================================
```

## Notes

- The starting balance is `Rs. 100,000.00`.
- Saved files are stored in the `data` folder.
- This project uses only Core Java and no external libraries.
