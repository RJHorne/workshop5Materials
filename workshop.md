# Workshop 5


**Classroom Link:** [https://classroom.github.com/a/K5d14Z9m](https://classroom.github.com/a/K5d14Z9m)



----------

## Part One - File name handling: Camels to Snakes

In some languages, it's common to use camel case (otherwise known as "mixed case") for variables' names when those names comprise multiple words, whereby the first letter of the first word is lowercase but the first letter of each subsequent word is uppercase.

For instance, whereas a variable for a user's name might be called `name`, a variable for a user's first name might be called `firstName`, and a variable for a user's preferred first name (e.g., nickname) might be called `preferredFirstName`.

Python, by contrast, recommends snake case, whereby words are instead separated by underscores (`_`), with all letters in lowercase. For instance, those same variables would be called `name`, `first_name`, and `preferred_first_name`, respectively, in Python.

**Task:** In the file called `camel.py`, implement a program that prompts the user for the name of a variable in camel case and outputs the corresponding name in snake case. Assume that the user's input will indeed be in camel case.

**Hint:** Recall that a `str` comes with quite a few methods, per Python Docs. Much like a list, a `str` is "iterable," which means you can iterate over each of its characters in a loop.

----------

## Part Two - The Coffee Machine (Prototype)

Imagine that you are thirsty and need a refreshing beverage, you see in the corner of your eye a Coffee machine. This coffee machine accepts cash only, and only **50p, 20p, 10p, 5p**.

**Task:** In the file called `coffee.py` implement a program that prompts the user to insert a coin, one at a time, each time informing the user of the amount due.

-   Once the user has inputted at least 75p, output how much change they are owed.
    
-   Make the assumption that the user will only enter integers, and ignore any unknown currency denomination.
    

----------

## Part Three – The Engineering Mindset: Requirements

_Stop coding for a moment._ In the lecture, we discussed how **85% of errors are made during requirement analysis and design**. Before we make the Coffee Machine more complex, we must formalize what it actually does to avoid "spaghetti code."

**Task:** Create a comment block at the top of your `coffee.py` file titled **"Statement of Requirements"**. Based on the code you wrote in Part Two, reverse-engineer the specifications. You must include:

1.  **Functional Requirements:** What inputs (specific coin integers) does the system accept? What is the exact output (change calculation)?
    
2.  **Non-Functional Requirements:** How should the system behave if the user inputs a string (e.g., "ten pence") instead of an integer? (This is a reliability requirement).
    

**Implementation Challenge:** Update your `coffee.py` to meet a new **reliability requirement**: The program must not crash if the user enters non-integer data. It should catch the error (using `try/except`), inform the user "Invalid Input," and ask for the coin again.

----------

## Part Four – Functional Decomposition (Refactoring)

The lecture introduced **Functional Decomposition**—breaking a problem down into smaller "chunks" or "primitives". Currently, your Coffee Machine is likely one long `while` loop. This is hard to maintain.

**Task:** Refactor (rewrite) your `coffee.py` solution by decomposing it into at least three separate functions. Consider the "Primitives" discussed in the lecture:

1.  `get_coin()`: Handles **Input data** (prompts user, checks validity).
    
2.  `update_total(current, coin)`: Performs **Simple calculations** (adds coin to total).
    
3.  `dispense_product(total_inserted)`: Handles **Output data** (calculates change, prints message).
    

Your main program flow should look clean, broadly resembling this:


```Python
def main():
    amount_due = 75
    while amount_due > 0:
        coin = get_coin()
        amount_due = update_total(amount_due, coin)
    dispense_product(amount_due)

```

----------

## Part Five – Iterative Design (The "Smart" Machine)

Now that you have a modular system (from Part Four), we are entering "Cycle 2" of the design. The client (University Cafeteria) wants to minimize the number of coins returned to the user as change.

**Task:**

1.  **Evaluate:** Run your current code. If a user is owed 15p, does it tell them "15p change" or "One 10p and one 5p"?
    
2.  **Modify:** Write a new algorithm called `calculate_change(amount)`.
    
    -   It should return the change using the largest available coin denominations first (e.g., 50p, 20p, 10p, 5p).
        
    -   _Example:_ If the user is owed 30p, the system should output "Returning: 20p, 10p".
        
3.  **Expansion (Optional):** Once you have a working smart machine, add more drinks to the system (Hot Chocolate, Tea) with different prices.
    

----------

## Part Six – Safety Critical Review

We looked at the **Ariane 5** and **Mars Lander** disasters caused by software errors.

**Task:** Look at your `camel.py` file from Part One.

1.  What happens if the user inputs a string containing numbers or symbols (e.g., `firstName123`)?
    
2.  In a "safety critical" version of this software, how would you ensure the variable name is valid before trying to convert it?
    
3.  Write a brief comment in your code explaining one "edge case" that could break your current logic.
