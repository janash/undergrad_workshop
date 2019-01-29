---
title: "Introduction"
teaching: 20
exercises: 10
questions:
- "What is the basic syntax of the python programming language?"
objectives:
- "Assign values to variables."
- "Use the print function to check how the code is working."
- "Use multiple assignment to assign several variables at once."
- "Use a for loop to perform the same action on the items in a list."
- "Use the append function to create new lists in for loops."
keypoints:
- "You can assign the values of several variables at once."
- "Indentation is very important in `for` loops and `if` statements.  Don't forget the `:` and to indent the items in the loop."
---
## Getting Started
Python is a computer programming language that has become ubiquitous in scientific programming.  Our initial lessons will run python *interactively* through a python interpreter.  The Startup page should have provided information
on how to start a python interpreter.  Everything included in a code block is something you could type into your python interpreter and evaluate.

## Assigning variables

Any python interpreter can work just like a calculator.  This is not very useful.

```
3+7
```
{: .language-python}

```
10
```
{: .output}

You can assign values to variable names and then you can use those variables in subsequent commands.  
```
deltaH = -541.5   #kJ/mole
deltaS =  10.4     #kJ/(mole K)
temp = 298      #Kelvin
deltaG = deltaH - temp*deltaS
print(deltaG)
```
{: .language-python}

```
-3640.7000000000003
```
{: .output}

Notice several things about this code.  The lines that begin with `#` are comment lines.  The computer does not do anything with these comments.  They have been used here to remind the user what units each of their values are in. Comments are also often used to explain what the code is doing, or leave information for future people who might use the code.

In the previous code block, we also introduced the `print()` function.  Often, we will use the print function just to make sure our code is working correctly.

Python can do what is called multiple assignment where you assign several variables their values on one line of code.  The following code block does the exact same thing as the previous code block.

```
#I can assign all these variables at once
deltaH, deltaS, temp = -541.5, 10.4, 298
deltaG = deltaH - temp*deltaS
print(deltaG)
```
{: .language-python}

```
-3640.7000000000003
```
{: .output}

Each variable is some particular type of data.  The most common types of data are strings, integers, and floats or floating point numbers.  In the code block below `label` is a string and `DeltaG` is a float.  It also shows how you can print more than one thing.
```
label = 'Delta G'    #this is a string
print(label, ':', deltaG)
```
{: .language-python}

```
Delta G : -3640.7000000000003
```
{: .output}

## Lists and Slices
Another common data structure in python is the list.  Lists can be used to group several values or variables together, and are declared using square brackets [ ]. List values are separated by commas. Python has several built in functions which can be used on lists. The built-in function `len` can be used to determine the length of a list.
```
#This is a list; I can determine it's length
energy_kcal = [-13.4, -2.7, 5.4, 42.1]
length = len(energy_kcal)
print('The length of this list is', length)
```
{: .language-python}

```
The length of this list is 4
```
{: .output}

If I want to operate on a particular element of the list, you use the list name and then put in brackets which element of the list you want.  **In python counting starts at zero.  So the first element of the list is `list[0]`**

```
print(energy_kcal[1])
```
{: .language-python}

```
-2.7
```
{: .output}

You can use an element of a list as a variable in a calculation.  
```
energy_kilojoules = energy_kcal[1]*4.184
print(energy_kilojoules)
```
{: .language-python}

```
-11.296800000000001
```
{: .output}

Sometimes you will want to make a new list that is a subset of an existing list.  For example, we might want to make a new list that is just the first few elements of our previous list.  This is called a `slice`.  The general syntax is
```
new_list = list_name[start:end]
```
{: .language-python}

When taking a slice, it is very important to remember how counting works in python.  Remember that counting starts at zero so the first element of a list is `list_name[0]`.  When you specify the last element for the slice, it goes *up to but not including* that element of the list.  So a slice like
```
short_list = energy_kcal[0:2]
```
{: .language-python}
includes energy_kcal[0] and energy_kcal[1] but *not* energy_kcal[2].
```
print(short_list)
```
{: .language-python}
```
[-13.4, -2.7]
```
{: .output}

If you do not include a start index, the slice automatically starts at `list_name[0]`.  If you do not include an end index, the slice automatically goes to the end of the list.  

> ## Check your Understanding
>
> What does the following code print?
> ~~~
> slice1 = energy_kcal[1:]
> slice2 = energy_kcal[:3]
> print('slice1 is', slice1)
> print('slice2 is', slice2)
> ~~~
> {: .language-python}
>
>> ## Answer
>>
>> ~~~
>> slice1 is [-2.7, 5.4, 42.1]
>> slice2 is [-13.4, -2.7, 5.4]
>> ~~~
>> {: .output}
> {: .solution}
{: .challenge}

## For loops
Often, you will want to do something to every element of a list.  The structure
to do this is called a `for` loop.  The general structure of a `for` loop is
```
for variable in list:
    do things using variable
```
{: .language-python}

Indentation is very important in python.  There is nothing like an `end` or `exit` statement that tells you that you are finished with the loop.  The indentation shows you what statements are in the loop.  Let's use a loop to change all of our energies in kcal to kJ.
```
for number in energy_kcal:
    kJ = number*4.184
    print(kJ)
```
{: .language-python}

```
-56.0656
-11.296800000000001
22.593600000000002
176.1464
```
{: .output}

Now it seems like we are really getting somewhere with our program!  But it would be even better if instead of just printing the values, it saved them in a new list.  To do this, we are going to use the `append` function.  The `append` function adds a new item to the end of an existing list.  The general form of the append function is
```
list_name.append(new_thing)
```
{: .language-python}

Try running this block of code.  See if you can figure out why it doesn't work.
```
for number in energy_kcal:
    kJ = number*4.184
    energy_kJ.append(kJ)

print(energy_kJ)
```
{: .language-python}
```
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-12-595146886489> in <module>()
      2 for number in energy_kcal:
      3     kJ = number*4.184
----> 4     energy_kJ.append(kJ)
      5
      6 print(energy_kJ)

NameError: name 'energy_kJ' is not defined
```
{: .error}

This code doesn't work because on the first iteration of our loop, the list `energy_kJ` doesn't exist.  To make it work, we have to start the list outside of the loop.  The list can be blank when we start it, but we have to start it.

```
energy_kJ = []
for number in energy_kcal:
    kJ = number*4.184
    energy_kJ.append(kJ)

print(energy_kJ)
```
{: .language-python}

```
[-56.0656, -12.1336, 22.593600000000002, 176.1464]
```
{: .output}

## A note about jupyter notebooks
If you use the jupyter notebook for your python interpreter, the notebook only executes the current code block.  This can have several unintended consequences. If you change a value and then go back and run an earlier code block, it will use the new value, not the first defined value, which may give you incorrect analysis.  Similarly, if you open your jupyter notebook later, and try to run a code block in the middle, it may tell you that your variables are undefined, even though you can clearly see them defined in earlier code blocks.  But if you didn't re-run those code blocks, then python doesn't know they exist.  

## Check Your Understanding

Insert some kind of activity here.

{% include links.md %}