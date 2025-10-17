<h1>ExpNo 8 : Solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python</h1> 
<h3>Name: YOGAVARMA B </h3>
<h3>Register Number :2305002029  </h3>
<H3>Aim:</H3>
<p>
    To solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python
</p>
<h3>Procedure:</h3>
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
Algorithm
For this problem, we will define a node, which contains a letter and its corresponding values.<br>

isValid(nodeList, count, word1, word2, word3)<br>

Input − A list of nodes, the number of elements in the node list and three words.<br>

Output − True if the sum of the value for word1 and word2 is same as word3 value.<br>

Begin<br>
   m := 1<br>
   for each letter i from right to left of word1, do<br>
      ch := word1[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>
      val1 := val1 + (m * nodeList[j].value)<br>
      m := m * 10<br>
   done<br>

   m := 1<br>
   for each letter i from right to left of word2, do<br>
      ch := word2[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>

      val2 := val2 + (m * nodeList[j].value)
      m := m * 10
   done<br>

   m := 1<br>
   for each letter i from right to left of word3, do<br>
      ch := word3[i]<br>
      for all elements j in the nodeList, do<br>
         if nodeList[j].letter = ch, then<br>
            break<br>
      done<br>

      val3 := val3 + (m * nodeList[j].value)
      m := m * 10
   done<br>

   if val3 = (val1 + val2), then<br>
      return true<br>
   return false<br>
End<br>

<hr>
<h2>Sample Input and Output:</h2>
SEND = 9567<br>
MORE = 1085<br>
<hr>
MONEY = 10652<br>

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

word1 = "EAT"
word2 = "THAT"
result = "APPLE"

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

<img width="649" height="220" alt="image" src="https://github.com/user-attachments/assets/acfca0cf-0395-4989-86a9-a9db157d089b" />




<hr>
<h2>Result:</h2>
<p> Thus a Cryptarithmetic Problem was solved using Python successfully</p>

