Pseudocode:

inputs:
- total: positive number - float (integer with decimals), bigger than 0 
- tipPercentage: positive number - float, between 0 and 100
process:
- calculateTip
output:
- newTotal (total + calculated tip): positive number - float (integer with decimals), bigger than 0
testCases:
----------
1.
input for total: 0
input for tip: 50
expected output: error message "total has to be bigger than 0" 
2.
total: 73
tip: 0
expected output: newTotal = 73.00
3.
total: 117.45 
tip: 13
expected output: newTotal = 132.70
4.
total: 117,45
tip: 13
expected output: newTotal = 132.70
5.
total: 69.70
tip: -5
expected output: error message "no negative values allowed"
6.
total: fivehundred
tip: zero
expected output: error message "numbers only"
7.
total: 350 CHF
tip: 5.5% / 5.5 %
expected output: error message "numbers only"
8. 
total: 120.43
tip: 1
expected output: 121.65  
Process:
========
1. Ask users for total and tip as 2 separate inputs
2. Check inputs values against constraints (number, positive, decimals either with "." or ",", and only for tip not bigger than 100, and only for total bigger than 0) 
2.a Continue to step 3
2.b Print warning (aka error) and go back to step 1
3. Calculate tip: total / 100 * tip 
4. Calculate new_total: total + calculatedTip
5. Print new_total formatted with 2 decimals plus currency
Refine process:
===============
Prompt "My total is " + inputTotal + " CHF."
Check inputTotal:
    Replace all , with .
    Convert to float
        If it does not works
            error = true
        Else 
            If inputTotal <= 0
                error = true
            Else
                continue
            End If
        End If
    If error
        Display "Please enter a positive number, e.g. 78.50"
        Go back to prompt
    End If
Prompt "My tip is " + inputTip + " %."
Check inputTip:
    Replace all , with .
    Convert to float
        If it does not works
            error = true
        Else 
            If inputTip < 0 OR inputTip > 100
                error = true
            Else
                continue
            End If
        End If
    If error
        Display "Please enter a positive number between 0 and 100"
        Go back to prompt
    End If
newTotal = inputTotal + (inputTotal / 100 * inputTip)
Round newTotal to either 0 or 5 on the 2nd decimal (aka Rappen)
Format newTotal to have 2 decimals
Print "Please pay " + newTotal + " CHF."