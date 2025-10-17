<h1>ExpNo 8 : Solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python</h1> 
<h3>Name: YOGAVARMA B </h3>
<h3>Register Number :2305002029  </h3>
<H3>Aim:</H3>
<p>
    To solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python
</p>
<h3>Procedure:</h3>
<p>
   Step 1: Start the program.

Step 2: Read three input words from the user —WORD1, WORD2, and RESULT.

Step 3: Combine all letters from the three words and find the unique letters.

a)If there are more than 10 unique letters → stop (since digits 0–9 can only represent 10 unique letters).

Step 4: Generate all possible digit assignments (permutations) for these unique letters.

Step 5: For each permutation:

  a) Create a mapping of each letter to a digit.

  b) Check if any leading letter of the three words is assigned 0 — if yes, skip this permutation.

  c) Convert each word into its numeric equivalent using the current mapping.

  d) Check if WORD1 + WORD2 == RESULT.

Step 6: If a valid mapping is found that satisfies the equation:

  a) Display the numeric values of WORD1, WORD2, and RESULT.

  b) Display the letter-to-digit mapping.

Step 7: If no valid mapping is found after checking all permutations, print “No solution found.”

Step 8: End the program. 
</p>
Input and Output
<br>Input:
This algorithm will take three words.
<br> B A S E<br>
    B A L L<br>
           ----------<br>
           G A M E S<br>

Output:
It will show which letter holds which number from 0 – 9.
For this case it is like this.

              B A S E                         2 4 6 1
              B A L L                         2 4 5 5
             ---------                       ---------
            G A M E S                       0 4 9 1 6

## PROGRAM
```Python
from itertools import permutations

def solve_cryptarithmetic(word1, word2, result):
 
    letters = set(word1 + word2 + result)
    if len(letters) > 10:
        print("Too many unique letters (max 10 allowed).")
        return None

    letters = list(letters)

    for perm in permutations(range(10), len(letters)):
        mapping = dict(zip(letters, perm))

        if mapping[word1[0]] == 0 or mapping[word2[0]] == 0 or mapping[result[0]] == 0:
            continue

        num1 = int("".join(str(mapping[ch]) for ch in word1))
        num2 = int("".join(str(mapping[ch]) for ch in word2))
        num_result = int("".join(str(mapping[ch]) for ch in result))

        if num1 + num2 == num_result:
            return num1, num2, num_result, mapping

    return None

word1 = input("Enter first word: ").upper()
word2 = input("Enter second word: ").upper()
result = input("Enter result word: ").upper()

solution = solve_cryptarithmetic(word1, word2, result)

if solution:
    num1, num2, num_result, mapping = solution
    print(f"\nSolution found!")
    print(f"{word1} = {num1}")
    print(f"{word2} = {num2}")
    print(f"{result} = {num_result}")
    print(f"Mapping: {mapping}")
else:
    print("No solution found.")
```

## output
<img width="826" height="315" alt="image" src="https://github.com/user-attachments/assets/8b55ad99-b9d7-4a8b-a38c-d4cd51e104f2" />




<hr>
<h2>Result:</h2>
<p> Thus a Cryptarithmetic Problem was solved using Python successfully</p>
