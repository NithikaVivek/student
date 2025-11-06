---
layout: post
title: MCQ
description: MCQ
permalink: /mcq-corrections
breadcrumb: true
toc: true
type: issues
---

# AP Computer Science A - MCQ Corrections & Analysis

## Summary Statistics
- Total Questions: 42
- Questions Incorrect: 17
- Score: 25/42
- Primary Weakness Areas: Loop Logic, Boolean Expressions, Array Manipulation, Recursion

<img src="{{ site.baseurl }}/images/Accuracy vs Unit.png" alt="Accuracy vs Unit">
<img src="{{ site.baseurl }}/images/Performance by Unit.png" alt="Performance by Unit">

| Unit | Total Questions | Correct | Wrong | Accuracy | Focus Areas |
|------|----------------|---------|-------|----------|-------------|
| Unit 1: Primitives | 7 | 6 | 1 | 85.7% | Strong performance overall |
| Unit 2: Control Structures | 12 | 7 | 5 | 58.3% | Review loops and conditionals |
| Unit 3: OOP | 6 | 4 | 2 | 66.7% | Practice class design |
| Unit 4: Arrays/ArrayLists | 17 | 8 | 9 | 47.1% | Focus on traversals & recursion |


---

## Q2: Compound Boolean Expression

**My Answer:** D  
**Correct Answer:** B

### Question
```java
boolean result = ((j > 0) && (k > 0)) || ((j < 0) && (k < 0));
```
Which best describes when result is true?

### Why I Was Wrong
I selected: "When j is positive and k is negative or when j is negative and k is positive"

This is the OPPOSITE of what the code does. Let's trace through with j=5, k=-3:
- First part: `(5 > 0) && (-3 > 0)` → `true && false` → **false**
- Second part: `(5 < 0) && (-3 < 0)` → `false && true` → **false**
- Final: `false || false` → **false**

### The Correct Answer
**B: When j and k are both positive or both negative**

The expression has TWO conditions connected by OR:
1. `(j > 0) && (k > 0)` - BOTH are positive
2. `(j < 0) && (k < 0)` - BOTH are negative

### Key Takeaway
Break down compound booleans step-by-step:
- `&&` means BOTH conditions must be true
- `||` means AT LEAST ONE condition must be true
- Draw a truth table if confused

---

## Q6: For Loop Printing Values

**My Answer:** B  
**Correct Answer:** A

### Question
```java
for (int j = 10; j >= 0; j -= 2)
{
   System.out.print(j - 1);
}
```
Should print: `97531` but doesn't work. What fix is needed?

### Current Output Trace
- j=10: prints 9
- j=8: prints 7
- j=6: prints 5
- j=4: prints 3
- j=2: prints 1
- j=0: prints -1

**Output:** `97531-1` (one extra value!)

### Why My Answer Was Wrong
I chose: "Change j = 10 to j = 9"

If j starts at 9:
- j=9: prints 8
- j=7: prints 6
- j=5: prints 4
- j=3: prints 2
- j=1: prints 0

**Output:** `86420` - completely wrong!

### The Correct Answer
**A: Change j >= 0 to j > 0**

This stops the loop BEFORE j reaches 0:
- j=10: prints 9
- j=8: prints 7
- j=6: prints 5
- j=4: prints 3
- j=2: prints 1
- j=0: loop stops (condition false)

**Output:** `97531` ✓

### Key Takeaway
Loop conditions matter! `>=` includes the boundary, `>` excludes it. Always trace through the LAST iteration to check if it should run.

---

## Q9: Measurement Class - Access Modifier Error

**My Answer:** B  
**Correct Answer:** C

### Question
```java
public class Measurement {
   private int feet;
   private int inches;
   
   private int toInches() { // PRIVATE method
      return feet * 12 + inches;
   }
}

public class Calculations {
   public static boolean compare(Measurement m1, Measurement m2) {
      if (m1.toInches() >= m2.toInches()) // Trying to call PRIVATE method
      {
         return true;
      }
      return false;
   }
}
```

### Why I Was Wrong
I selected: "The compare method should be declared as void"

But the method NEEDS to return a boolean! It's comparing two measurements and telling which is larger. A void method can't return anything.

### The Correct Answer
**C: The toInches method cannot be accessed from a class other than Measurement**

The `toInches()` method is **private**, meaning only code INSIDE the Measurement class can call it. The Calculations class is trying to access it from OUTSIDE.

### The Fix
Change `private int toInches()` to `public int toInches()`

### Key Takeaway
**Access Modifiers:**
- `private` - only accessible within the same class
- `public` - accessible from anywhere
- If I need to call a method from another class, it must be public!

---

## Q10: If Statements for Score Messages

**My Answer:** D  
**Correct Answer:** A

### Question
Requirements:
- score > 500 → "Great!"
- 250 ≤ score ≤ 500 → "Good!"
- score < 250 → "Try again."

### Why My Answer Was Wrong
```java
if (score > 500) {
   message = "Great!";
}
else if (score <= 500) { // This catches EVERYTHING else!
   message = "Good!";
}
else {
   message = "Try again."; // Never reached!
}
```

If score = 100:
- Is 100 > 500? No
- Is 100 <= 500? **YES** → assigns "Good!" (WRONG!)
- The else never runs because 100 <= 500 is true

The else clause is unreachable because ALL scores are either > 500 or <= 500.

### The Correct Answer
```java
if (score < 250) {
   message = "Try again.";
}
else if (score <= 500) { // Only reaches here if score >= 250
   message = "Good!";
}
else { // Only reaches here if score > 500
   message = "Great!";
}
```

### Why This Works
- score = 100: Is 100 < 250? **YES** → "Try again." ✓
- score = 300: Is 300 < 250? No. Is 300 <= 500? **YES** → "Good!" ✓
- score = 600: Is 600 < 250? No. Is 600 <= 500? No. → "Great!" ✓

### Key Takeaway
Order matters in if-else chains! Once a condition is true, the rest are skipped. Use mutually exclusive conditions or check ranges in the right order (smallest to largest OR largest to smallest, but be consistent).

---

## Q16: Book Class Design Diagram

**My Answer:** C  
**Correct Answer:** D

### OOP Design Principles
A well-designed class should:
1. Keep data **private** (encapsulation)
2. Provide **public** methods to access data (getters)

### Why My Answer Was Wrong
Option C had:
- **PUBLIC** instance variables (+title, +author, +numPages)
- **PRIVATE** getter methods (-getTitle(), -getAuthor(), -getNumPages())

This is backwards! If the variables are public, anyone can access them directly, which violates encapsulation. If the getters are private, no one can use them, which defeats their purpose.

### The Correct Answer
Option D:
```
Book
-----------
- title : String        // PRIVATE data
- author : String
- numPages : int
-----------
+ getTitle() : String   // PUBLIC getters
+ getAuthor() : String
+ getNumPages() : int
```

### Why This Design is Correct
- Private variables prevent direct external modification
- Public getters allow controlled read access
- I can later add validation or change internal structure without breaking external code

### Key Takeaway
**Standard OOP pattern:**
- Instance variables: **PRIVATE** (-)
- Getter/Setter methods: **PUBLIC** (+)
- This is called **encapsulation** - hiding internal details while providing controlled access

---

## Q17: System Reliability Action

**My Answer:** C  
**Correct Answer:** B

### Question
What action most supports system reliability?

### Why I Was Wrong
I selected: "Using public visibility for the attributes used in the application"

Making attributes public actually **HURTS** reliability because:
- Any code can modify the data directly
- No validation can be enforced
- Hard to track bugs (who changed what?)
- Breaks encapsulation

### The Correct Answer
**B: Testing the application under a wide variety of possible conditions**

System reliability means the software works correctly under various scenarios:
- Different devices (phones, tablets, screen sizes)
- Different network conditions (slow, fast, offline)
- Different user inputs (edge cases, invalid data)
- Different languages and regions
- High load conditions

Testing catches bugs before users encounter them.

### Key Takeaway
**System Reliability = Thorough Testing**
- Unit tests (individual methods)
- Integration tests (components working together)
- Edge case testing (boundary values, null, empty, negative)
- Stress testing (many users, large data)

---

## Q18: findMaximum Method Error

**My Answer:** B  
**Correct Answer:** C

### Question
```java
public static int findMaximum(int[] numbers) {
   int max = 0;  // Problem: initialized to 0
   for (int num : numbers) {
      if (num > max) {
         max = num;
      }
   }
   return max;
}
```

### Why My Answer Was Wrong
I selected: "When the maximum value appears multiple times"

Let's test with `{5, 10, 10}`:
- max starts at 0
- Check 5: 5 > 0? Yes → max = 5
- Check 10: 10 > 5? Yes → max = 10
- Check 10: 10 > 10? No → max stays 10
- Return 10 ✓

Multiple occurrences work fine!

### The Correct Answer
**C: When the maximum value is negative**

Test with `{-50, -20, -100}`:
- max starts at 0
- Check -50: -50 > 0? **No** → max stays 0
- Check -20: -20 > 0? **No** → max stays 0
- Check -100: -100 > 0? **No** → max stays 0
- Return 0 ✗ (should return -20)

### The Fix
```java
int max = numbers[0]; // Initialize to first element
// OR
int max = Integer.MIN_VALUE; // Initialize to smallest possible int
```

### Key Takeaway
**Finding max/min:**
- NEVER initialize to 0 unless I'm sure all values are positive
- Initialize to the first element OR use Integer.MIN_VALUE/Integer.MAX_VALUE
- This is a classic bug pattern!

---

## Q19: Random Number Generation

**My Answer:** D  
**Correct Answer:** C

### Question
```java
int r = (int) (Math.random() * 6) + 10;
```

### Breaking Down Math.random()
- `Math.random()` returns a double from **[0.0, 1.0)** (0.0 inclusive, 1.0 exclusive)
- Multiply by 6: **[0.0, 6.0)**
- Cast to int: **[0, 5]** (truncates decimal)
- Add 10: **[10, 15]**

### Why My Answer Was Wrong
I selected: "Between 10 and 16, inclusive"

To get values up to 16, I'd need:
```java
int r = (int) (Math.random() * 7) + 10; // Multiply by 7, not 6
```

### The Correct Answer
**C: Between 10 and 15, inclusive**

**Step-by-step:**
1. Math.random() = 0.0 → 0 * 6 = 0 → (int)0 = 0 → 0 + 10 = **10**
2. Math.random() = 0.5 → 0.5 * 6 = 3.0 → (int)3 = 3 → 3 + 10 = **13**
3. Math.random() = 0.9999 → 0.9999 * 6 = 5.9994 → (int)5 = 5 → 5 + 10 = **15**

### The Pattern
```java
(int)(Math.random() * N) + start
```
- Generates N different values
- Range: [start, start + N - 1]

To get [10, 15]: N = 6, start = 10

### Key Takeaway
**Random int formula: `(int)(Math.random() * range) + min`**
- range = max - min + 1
- For [10, 15]: range = 15 - 10 + 1 = 6

---

## Q20: Division and Modulus in Loop

**My Answer:** D  
**Correct Answer:** C

### Question
```java
int value = 100;
while (value % 5 == 0) {
   value /= 2;
}
System.out.println(value);
```

### Trace Through Execution
1. value = 100; 100 % 5 = 0 → continue
2. value = 100 / 2 = 50; 50 % 5 = 0 → continue
3. value = 50 / 2 = 25; 25 % 5 = 0 → continue
4. value = 25 / 2 = **12** (integer division!); 12 % 5 = 2 → **STOP**
5. Print 12

### Why My Answer Was Wrong
I selected: 100

The loop DOES execute! The condition `value % 5 == 0` is true initially (100 is divisible by 5), so the loop runs.

### The Correct Answer
**C: 25**

Wait, I traced it to 12... Let me re-trace:
1. value = 100; 100 % 5 = 0 ✓
2. value = 50; 50 % 5 = 0 ✓
3. value = 25; 25 % 5 = 0 ✓
4. value = 12; 12 % 5 = 2 ✗ STOP

Actually prints **12**, but let me check the answer key again...

Hmm, if the correct answer is 25, let me re-check:
- After value becomes 25, check 25 % 5 = 0 (true)
- value = 25 / 2 = 12
- Check 12 % 5 = 2 (false)
- Exit loop
- Print 12

**Note:** There may be an error in the original answer key. Based on the code, 12 should be printed, not 25.

### Key Takeaway
**Trace loops step-by-step:**
1. Write current value
2. Check condition
3. Execute body if true
4. Update value
5. Repeat until condition false

---

## Q21: Missing Inner For Loop Header

**My Answer:** A  
**Correct Answer:** B

### Question
```java
for (int j = 0; j < 4; j++) {
   for (/* missing code */) {
      System.out.print(j + " ");
   }
   System.out.println();
}
```

### Desired Output
```
0
1 1
2 2 2
3 3 3 3
```

### Why My Answer Was Wrong
**My answer: `int k = 0; k < j; k++`**

Let's trace:
- j=0: k loops from 0 to 0 (k < 0 is false immediately) → prints nothing
- j=1: k loops 0 times (k < 1 means k=0) → prints "1" once
- j=2: k loops twice (k=0,1) → prints "2 2"
- j=3: k loops 3 times (k=0,1,2) → prints "3 3 3"

Output:
```

1
2 2
3 3 3
```

Missing one value on each line!

### The Correct Answer
**B: `int k = 0; k <= j; k++`**

The key difference is `<=` instead of `<`:
- j=0: k loops from 0 to 0 (k=0, then k++ makes k=1, 1 <= 0 is false) → prints "0" once ✓
- j=1: k loops for k=0,1 → prints "1 1" ✓
- j=2: k loops for k=0,1,2 → prints "2 2 2" ✓
- j=3: k loops for k=0,1,2,3 → prints "3 3 3 3" ✓

### Key Takeaway
**Boundary conditions:**
- `k < n` → loops n times (0 to n-1)
- `k <= n` → loops n+1 times (0 to n)
- When I need to print j exactly j+1 times, use `k <= j`

---

## Q26: Print Leftmost Digit

**My Answer:** D  
**Correct Answer:** A

### Question
```java
while (n > 0) {
   n /= 10;
}
System.out.println(n);
```

Should print leftmost digit of n (e.g., 302 → 3).

### Current Behavior
With n=302:
- n=302: 302 > 0 → n = 30
- n=30: 30 > 0 → n = 3
- n=3: 3 > 0 → n = 0
- n=0: 0 > 0 is false → exit
- Print 0 ✗

The loop goes TOO FAR - it reduces n to 0!

### Why My Answer Was Wrong
**I chose: Change `n /= 10` to `n %= 10`**

This gets the rightmost digit, not leftmost!
- 302 % 10 = 2 (last digit)
- 302 / 10 = 30 (removes last digit)

With `n %= 10`:
- n=302: 302 > 0 → n = 302 % 10 = 2
- n=2: 2 > 0 → n = 2 % 10 = 2
- Infinite loop! (2 never becomes 0)

### The Correct Answer
**A: Change `n > 0` to `n / 10 > 0`**

This stops when n has only one digit left:
- n=302: 302/10 = 30, 30 > 0 → continue, n = 30
- n=30: 30/10 = 3, 3 > 0 → continue, n = 3
- n=3: 3/10 = 0, 0 > 0 is false → **STOP**
- Print 3 ✓

### Key Takeaway
**Getting leftmost digit:**
- Keep dividing by 10 until only one digit remains
- Stop when `n / 10 == 0` (or `n / 10 > 0` is false)
- Don't use %, that's for rightmost digit!

---

## Q29: Recursive printNums Method

**My Answer:** B  
**Correct Answer:** C

### Question
```java
public static void printNums(int n) {
   if (n < 50) {
      printNums(n * -2);
      System.out.print(n + " ");
   }
}
```

Call: `printNums(10)`

### Why My Answer Was Wrong
I selected: "10 -20 40 -80"

This would be correct if the print happened BEFORE the recursive call. But look carefully - the print is AFTER!

### Tracing Recursion
**Call stack (going down):**
1. printNums(10): 10 < 50 ✓ → call printNums(10 * -2 = -20)
2. printNums(-20): -20 < 50 ✓ → call printNums(-20 * -2 = 40)
3. printNums(40): 40 < 50 ✓ → call printNums(40 * -2 = -80)
4. printNums(-80): -80 < 50 ✓ → call printNums(-80 * -2 = 160)
5. printNums(160): 160 < 50? **NO** → return (don't print)

**Unwinding (going back up, printing happens now):**
4. Print -80
3. Print 40
2. Print -20
1. Print 10

### The Correct Answer
**C: "40 -20 10"**

Wait, let me recheck... Actually based on my trace, it should be "-80 40 -20 10". But if -80 is printed, something's off.

Let me retrace more carefully:
- printNums(10) → calls printNums(-20) → calls printNums(40) → calls printNums(-80) → calls printNums(160)
- printNums(160): condition false, returns without printing
- Back to printNums(-80): prints "-80"
- Back to printNums(40): prints "40"
- Back to printNums(-20): prints "-20"
- Back to printNums(10): prints "10"

Output should be: "-80 40 -20 10"

But answer C is "40 -20 10"... 

Ah! Let me check if -80 < 50:
-80 < 50 is TRUE (negative numbers are less than positive)

So printNums(-80) DOES make a recursive call to printNums(160), and 160 < 50 is FALSE, so it returns without doing anything.

Then -80 gets printed. So the full output is "-80 40 -20 10".

**There may be an issue with the answer key provided.**

### Key Takeaway
**Recursion printing:**
- Print BEFORE recursive call → prints on the way down (forward)
- Print AFTER recursive call → prints on the way up (backward)
- Always trace the call stack completely!

---

## Q33: Array Traversal Contents

**My Answer:** C  
**Correct Answer:** B

### Question
```java
int[] arr = {10, 20, 30, 40, 50, 60};
for (int j = arr.length - 1; j >= 0; j -= 2) {
   arr[j]++;
}
```

### Tracing the Loop
Starting j = arr.length - 1 = 5, decrement by 2 each time:

- j=5: arr[5]++ → arr[5] = 60+1 = 61 → `{10, 20, 30, 40, 50, 61}`
- j=3: arr[3]++ → arr[3] = 40+1 = 41 → `{10, 20, 30, 41, 50, 61}`
- j=1: arr[1]++ → arr[1] = 20+1 = 21 → `{10, 21, 30, 41, 50, 61}`
- j=-1: j >= 0 is false → STOP

Final: `{10, 21, 30, 41, 50, 61}`

### Why My Answer Was Wrong
I selected: `{10, 20, 31, 40, 51, 60}`

This would happen if the loop went from left to right starting at index 2 and incrementing by 2. But the loop goes RIGHT TO LEFT (j -= 2) starting at the END (j = arr.length - 1).

### The Correct Answer
**B: `{10, 21, 30, 41, 50, 61}`**

The loop modifies indices 5, 3, 1 (every other element from right to left).

### Key Takeaway
**Array traversal:**
- Forward: `for (int i = 0; i < arr.length; i++)`
- Backward: `for (int i = arr.length - 1; i >= 0; i--)`
- Every other element: increment/decrement by 2
- Always trace with actual indices to avoid confusion!

---

## Q34: Build newList from oldList

**My Answer:** D  
**Correct Answer:** B

### Question
```
oldList = ["a", "b", "c"]
newList should become = ["c", "b", "a", "a", "b", "c"]
```

Pattern: reversed oldList + normal oldList

### Why My Answer Was Wrong
**Option D:**
```java
for (int j = 0; j < oldList.size(); j++) {
   newList.add(j, oldList.get(j));
   newList.add(0, oldList.get(j));
}
```

Trace:
- j=0: add "a" at index 0 → `["a"]`, then add "a" at index 0 → `["a", "a"]`
- j=1: add "b" at index 1 → `["a", "b", "a"]`, then add "b" at index 0 → `["b", "a", "b", "a"]`
- j=2: add "c" at index 2 → `["b", "a", "c", "b", "a"]`, then add "c" at index 0 → `["c", "b", "a", "c", "b", "a"]`

Result: `["c", "b", "a", "c", "b", "a"]` - close but wrong order!

### The Correct Answer
**Option B:**
```java
for (String s : oldList) {
   newList.add(s);      // Add to end
   newList.add(0, s);   // Add to beginning
}
```

Trace:
- s="a": add "a" → `["a"]`, add "a" at 0 → `["a", "a"]`
- s="b": add "b" → `["a", "a", "b"]`, add "b" at 0 → `["b", "a", "a", "b"]`
- s="c": add "c" → `["b", "a", "a", "b", "c"]`, add "c" at 0 → `["c", "b", "a", "a", "b", "c"]` ✓

### Key Takeaway
**ArrayList.add() behavior:**
- `add(element)` - adds to END
- `add(0, element)` - adds to BEGINNING (shifts everything right)
- Adding to beginning during iteration builds a reversed list!

---

## Q37: 2D Array enigma Method

**My Answer:** C  
**Correct Answer:** D

### Question
```java
public static int enigma(int[][] values, int x, int target) {
   int result = 0;
   for (int num : values[x]) {
      if (num == target) {
         result++;
      }
   }
   return result;
}
```

### Why My Answer Was Wrong
I selected: "The number of times target appears in **column** x"

But look at the loop: `for (int num : values[x])`

- `values[x]` is the entire ROW at index x (not column!)
- In a 2D array, the first index is the row, second is the column

### The Correct Answer
**D: The number of times target appears in **row** x**

Example:
{% raw %}
```
values = {{1, 2, 3},
          {4, 5, 4},
          {7, 8, 9}}
          
enigma(values, 1, 4) looks at values[1] = {4, 5, 4}
Counts how many times 4 appears in row 1 → returns 2
```
{% endraw %}

### Key Takeaway
**2D Array indexing:**
- `array[row][col]` - row first, column second
- `array[i]` - entire row i
- To access a column, I need a loop: `for (int i = 0; i < array.length; i++) { array[i][col] }`

---

## Q38: Scanner with File Splitting

**My Answer:** Not specified  
**Correct Answer:** C

Based on the code pattern shown, the correct answer involves using `split("_")` to separate the two parts of each line.

**Correct Answer:** C

```java
while (sc.hasNext()) {
   String[] temp = sc.next().split("_");
   firstList.add(temp[0]);
   secondList.add(temp[1]);
}
```

This reads each word, splits it by underscore, and adds the first part to firstList and second part to secondList.

### Key Takeaway
**String.split(delimiter):**
- Returns an array of strings
- `"finest_artist".split("_")` → `["finest", "artist"]`
- `temp[0]` is the first part, `temp[1]` is the second

---

## Q39: Recursive Binary Search

**My Answer:** Not specified  
**Correct Answer:** D (value is 2)

### Question
```java
int[] numbers = {10, 10, 10, 20, 20, 30, 40, 50, 50, 60, 80};
int result = binarySearch(numbers, 0, numbers.length - 1, 10);
```

### Tracing Binary Search for target=10
1. low=0, high=10, mid=(0+10)/2=5
   - numbers[5]=30
   - 10 < 30 → search left half: binarySearch(numbers, 0, 4, 10)

2. low=0, high=4, mid=(0+4)/2=2
   - numbers[2]=10
   - 10 == 10 → **return 2** ✓

### The Answer
**D: 2**

The method finds 10 at index 2 (note: there are multiple 10s, but binary search returns the first one it finds, which happens to be at index 2).

### Key Takeaway
**Binary search:**
- Only works on SORTED arrays
- Returns ONE valid index (may not be the first occurrence)
- Runs in O(log n) time
- Each step eliminates half the remaining elements

---

## Performance Analysis by Topic

### Boolean Logic (1 question)
- Q2: Compound boolean expressions
- **Weakness:** Not tracing through each part of compound expressions
- **Fix:** Draw truth tables, evaluate each clause separately

### Loop Logic (5 questions)
- Q6: For loop boundary conditions
- Q20: While loop with division/modulus
- Q21: Nested loop iteration counts
- Q26: Loop termination conditions
- Q33: Array traversal patterns
- **Weakness:** Not tracing loops step-by-step, especially boundary cases
- **Fix:** Always trace first, middle, and last iterations

### Access Modifiers (2 questions)
- Q9: Private method access
- Q16: Class design encapsulation
- **Weakness:** Forgetting private members can't be accessed from other classes
- **Fix:** Remember: private = same class only, public = anywhere

### Conditionals (1 question)
- Q10: If-else chain logic
- **Weakness:** Not considering which branches are reachable
- **Fix:** Test with values that should hit each branch

### Arrays (4 questions)
- Q18: Array algorithm with initialization bug
- Q33: Array modification during traversal
- Q34: ArrayList manipulation
- Q37: 2D array row vs column
- **Weakness:** Confusion about indexing and traversal direction
- **Fix:** Draw arrays visually, mark indices

### Recursion (2 questions)
- Q29: Recursive call order and printing
- Q39: Binary search recursion
- **Weakness:** Not tracking call stack and when printing occurs
- **Fix:** Draw call stack, mark "going down" vs "coming back up"

### String/File Processing (1 question)
- Q38: Scanner with String.split()
- **Weakness:** Not familiar with split() method
- **Fix:** Practice string parsing methods

### Miscellaneous (2 questions)
- Q17: Software engineering practices
- Q19: Random number generation formula

---

## Overall Improvement Strategy

### 1. TRACE EVERYTHING
Never try to "figure out" code in my head. Write it down:
- For loops: write j values for first 3-4 iterations
- Arrays: draw the array with indices
- Recursion: draw the call stack
- Booleans: evaluate each part separately

### 2. Test Edge Cases
Always check:
- Empty collections
- Single element
- All negative numbers
- Boundary values (0, max, min)
- First and last iterations of loops

### 3. Master the Patterns
Memorize these common patterns: