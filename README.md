# budget-tracker-design
budget tracker pseudocode and IPO chart

**Course:** ITP 100 Software Design and Logic  
**Author:** Sahel Khan  
**Deliverable:** Algorithm Design (IPO chart, Psuedocode)  

## 1. Problem Description & Scope   
**Problem** Students need a command-line interface to track income, expenses, categories, and monthly profit/loss
**Scope** 
  * Featuers a continouis main loop with 2 hireahical submenus (Income and expenses).
  *  Validates menu choices (reject 0 value outside menu options) and money amounts (rejects negitive inputs).
  *  Keeps track of total income and total expenses during execution and displays a financial summary.
  * Calculates whether the user made a profit, loss, or broke even.
  * Terminates cleanly when the user selects the Exit option.

## 2. IPO Chart (Input - Process - Output) 
| Input | Processing | Output |
|:---|:---|:---|
| `main_choice` (Integer: 1-4)<br>`sub_choice` (Integer: 1-3)<br>`amount` (Real: >= 0) | 1. Initialize `total_income = 0`, `total_expenses = 0`.<br>2. Loop main menu until user enters `4`.<br>3. Validate that `main_choice` is between 1 and 4.<br>4. If `1` (Income):<br>&emsp;a. Display income submenu.<br>&emsp;b. Validate `sub_choice` between 1 and 3.<br>&emsp;c. Prompt for amount; loop until `amount >= 0`.<br>&emsp;d. Match choice to income category.<br>&emsp;e. Add `amount` to `total_income`.<br>5. If `2` (Expense):<br>&emsp;a. Display expense submenu.<br>&emsp;b. Validate `sub_choice` between 1 and 3.<br>&emsp;c. Prompt for amount; loop until `amount >= 0`.<br>&emsp;d. Match choice to expense category.<br>&emsp;e. Add `amount` to `total_expenses`.<br>6. If `3` (Summary):<br>&emsp;a. Calculate `net_balance = total_income - total_expenses`.<br>&emsp;b. Compare `net_balance` to `0`.<br>7. If `4`, exit the program. | Main menu<br>Income menu<br>Expense menu<br>Invalid choice messages<br>Invalid amount messages<br>Income confirmation message<br>Expense confirmation message<br>Total income<br>Total expenses<br>Net balance<br>Profit, loss, or break-even status message<br>Exit message | 
- - -

 ## 3. Pseudocode

Module Main()

DECLARE Real design_income = 0
DECLARE Real coding_income = 0
DECLARE Real documentation_income = 0

DECLARE Real software_expense = 0
DECLARE Real equipment_expense = 0
DECLARE Real workspace_expense = 0

DECLARE Real total_income = 0
DECLARE Real total_expenses = 0
DECLARE Real net_balance = 0

DECLARE Integer main_choice = 0
DECLARE Integer sub_choice = 0
DECLARE Real amount = 0

    DISPLAY "=========================================="
    DISPLAY "         PERSONAL BUDGET TRACKER"
    DISPLAY "=========================================="

    WHILE main_choice != 4

        DISPLAY "--- MAIN MENU ---"
        DISPLAY "1. Log Income"
        DISPLAY "2. Log Expense"
        DISPLAY "3. View Financial Summary"
        DISPLAY "4. Exit"
        DISPLAY "Enter your choice (1-4):"
        INPUT main_choice

        WHILE main_choice < 1 OR main_choice > 4
            DISPLAY "Invalid. Choice must be 1, 2, 3, or 4. Try Again:"
            INPUT main_choice
        END WHILE


        IF main_choice == 1 THEN

            DISPLAY "--- INCOME MENU ---"
            DISPLAY "1. Design"
            DISPLAY "2. Coding"
            DISPLAY "3. User Documentation"
            DISPLAY "Enter income category:"
            INPUT sub_choice

            WHILE sub_choice < 1 OR sub_choice > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            DISPLAY "Enter income amount ($):"
            INPUT amount

            WHILE amount < 0
                DISPLAY "Invalid. Please enter amount >= 0:"
                INPUT amount
            END WHILE

            IF sub_choice == 1 THEN
                SET category_name = "Design"
                SET design_income = design_income + amount

            ELSE IF sub_choice == 2 THEN
                SET category_name = "Coding"
                SET coding_income = coding_income + amount

            ELSE
                SET category_name = "User Documentation"
                SET documentation_income = documentation_income + amount
            END IF

            DISPLAY "Successfully added $ ", amount, " for ", category_name, "."


        ELSE IF main_choice == 2 THEN

            DISPLAY "--- EXPENSE MENU ---"
            DISPLAY "1. Software"
            DISPLAY "2. Equipment"
            DISPLAY "3. Workspace"
            DISPLAY "Enter expense category:"
            INPUT sub_choice

            WHILE sub_choice < 1 OR sub_choice > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            DISPLAY "Enter expense amount ($):"
            INPUT amount

            WHILE amount < 0
                DISPLAY "Invalid. Please enter amount >= 0:"
                INPUT amount
            END WHILE

            IF sub_choice == 1 THEN
                SET category_name = "Software"
                SET software_expense = software_expense + amount

            ELSE IF sub_choice == 2 THEN
                SET category_name = "Equipment"
                SET equipment_expense = equipment_expense + amount

            ELSE
                SET category_name = "Workspace"
                SET workspace_expense = workspace_expense + amount
            END IF

            DISPLAY "Successfully added $ ", amount, " for ", category_name, "."


        ELSE IF main_choice == 3 THEN

            SET total_income = design_income + coding_income + documentation_income

            SET total_expenses = software_expense + equipment_expense + workspace_expense

            SET net_balance = total_income - total_expenses

            DISPLAY "=========================================="
            DISPLAY "          FINANCIAL SUMMARY"
            DISPLAY "=========================================="
            DISPLAY "Total Income:   $", total_income
            DISPLAY "Total Expenses: $", total_expenses
            DISPLAY "Net Balance:    $", net_balance

            IF net_balance > 0 THEN
                DISPLAY "Status: You are profitable this month!"

            ELSE IF net_balance < 0 THEN
                DISPLAY "Status: You had a loss this month!"

            ELSE
                DISPLAY "Status: You broke even this month!"
            END IF

            DISPLAY "=========================================="


        ELSE IF main_choice == 4 THEN

            DISPLAY "Thank you for using Personal Budget Tracker. Goodbye!"
            BREAK

        END IF

    END WHILE

End Module
