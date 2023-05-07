**Intro to Ruby Book - Ch 2 - Variables - Exercise 5**

# Problem:

Look at the following programs.
What does x print to the screen in each case? Do they both give errors? Are the errors different? Why?

# Note: 

This is a markdown file format to describe and speculate on Exercise 5
Reference variables_5_code1.arb and variables_5_code2.arb to run the provided code.

**Program 1:**

```ruby
x = 0
3.times do
  x += 1
end
puts x
```

**Program 2:**

```ruby
y = 0
3.times do
  y += 1
  x = y
end
puts x
```

# Prior to running the code in pry, these are my guesses about what the errors will be related to:

**Program 1:**

There will be an error related to missing an inner scope block variable placeholder.
This would be neccessary to provide access to the local x variable that was defined in the outer scope.
The facts that the puts statement exists in the outer scope helps to create that issue.
If puts was in the inner scope, preceding x += 1, I think the program might run correctly.

**Problem 2:**

The same guess described above for Problem 1 would apply here for the y variable and outer scope puts statement.
For the x variable in problem 2, there would be an error along the lines of "could not find local variable" or "local variable does not exist" or something like that.
My guess is that this would occur for x since it was never defined in the outer scope.

# After running the code in pry, these are the errors that were outputted:

**Problem 1:**

No error output. Output is:

3

**Problem 2:**

Traceback (most recent call last):
variables_5_code2.arb:6:in `<main>': undefined local variable or method `x' for main:Object (NameError)

**Conclusions:**

Program 1:

There were no errors in this program, and the output was 3. My initial assumption about the inner scope block variable placeholder was incorrect. The variable x is defined in the outer scope and is accessible within the do...end block. The block does create a new scope, but variables from the outer scope are still accessible within the block.

Program 2:

The initial assumption about the y variable was incorrect, as it is defined in the outer scope and accessible within the block without causing any errors.
For this program, a NameError was raised due to the variable x being defined within the block and not being accessible in the outer scope where the puts x statement is located. A block variable placeholder for x is necessary because the variable x was defined within the block instead of the outer scope. Since the variable x was defined within the block, it is only accessible within the block. In this scenario, because the puts statement is outside the block, an error occurs since the variable x is not accessible in the outer scope.

# Key Takeaway:

The key takeaway is that the do...end syntax is used to define a block, and the block can create a new scope for variables. However, if a variable is already defined in the outer scope, it is accessible within the block without needing an inner scope block variable placeholder. The distinction between inner and outer scopes exists, but variables defined in the outer scope can be accessed and modified within the block.