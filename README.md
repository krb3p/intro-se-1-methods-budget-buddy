# Budget Buddy

## The Goal

Today we're going to write a program that can help make sure you don't ever accidentally spend too much money at the grocery store by writing a budget app.

A budget is a breakdown of where you plan to spend your money before you actually spend it - it can be easy to spend money on fun things the day you get your paycheck, because it feels like you have all this extra money!

![Homer spends too much on donuts](SimpBudget.gif)

However, it's important to remember to keep money aside for important purchases like groceries, or to save it up for something that matters to you.

If you want more context on what budgeting is and why people do it before starting the lab, you can learn more <a href="http://kwhs.wharton.upenn.edu/2015/02/zina-kumoks-top-5-budget-tips/">here</a>.

## Our Program

We're going to create several different budget checkers. Each one will let a user enter their total before they swipe their card or hand over cash at the register, just to make sure they're not about to overspend.

Some users will want it super simple, so we will write a simple budget checker for them. It will only give them a message if they're about to spend too much money.

Other users will want to know how much money they have left to spend, or how far over budget they are. That's a more complex tool, so we will build it after we've got the simple one done.

We'll start with a budget of 100 dollars, meaning we can spend that much according to our plan. Anything over 100 dollars is considered overspending.

## Defining and Testing

This lab is broken into two parts. The definitions of all our budgets will be in a file called budget.rb. We're only DEFINING budgets checkers here, not testing them yet.

We will TEST our budget checkers using the budgetTest.rb file. We can run those tests with the command `ruby budgetTest.rb` in our console / terminal / command line.

If you feel ready to jump into the lab, then go for it! If you'd like a little refresher or if you get stuck, read on through the main concepts the lab will cover.

## Useful Skills & Vocab

### Defining versus calling methods

Implementing methods in a program is a two-step process. Methods must first be defined and then they can be called.

###### Defining

```ruby
def my_test_method
  return "Hello! Your test has run successfully!"
end
```

###### Calling

```ruby
puts my_test_method
```

If a method is never called, then your program COULD use it, but it never knows when to do so.

### Returning versus printing output

We're relying on returning output when we define our methods, but we're using print statements in our tests so that those return values are visible. Remember, printed data can be seen, returned data can stored in variables or otherwise used.

For a refresher course on the difference, jump back to the <a href="https://github.com/upperlinecode/intro-se-1-methods-string-methods">String Music Theory lab</a> and read over the notes on printing v. returning.

### Using multiple arguments

One of the more advanced budget checkers will take two arguments. For example, if you wanted to know how much it costs to buy a family tickets to Disneyland, you'd need TWO pieces of information.

Take a look at this screenshot from Disney's website:

![Disney Tickets Screenshot](DisneyTix.png)

You need to know how many adults (considered 10 years old or older) and how many children (ages 3-9) will be attending. SO let's write out the definition of that method.

```ruby
def cost_of_disney(adults, children)
  adult_price = adults * 199
  child_price = children * 187
  total_cost = adult_price + child_price
  return total_cost
end
```

Now that we can calculate the cost of tickets, let's do that for this family:

![Disney Family](WDW-family.jpg)

Let's assume the two smaller children are both between the ages of 3 and 9, so then this family has 6 adults and 2 children.

Find the total cost by calling (and printing!) the method.

```ruby
puts cost_of_disney(6, 2)
```

### Scope

Fascinatingly, entering a method definition is like entering a pocket dimension - only the information passed to it will exist. All other variables will be prevented from entering the method. Here are two examples of BAD CODE - code that will fail to run as a result of improper scoping.

###### Variable scoped outside a method

```ruby
greeting = "Welcome to the program"

def start
  return greeting # Since we're in a pocket dimension of sorts, this method doesn't know about the string we just stored in a variable above. The code will break here.
end

# don't forget to call the method!
puts start
```

###### Variable scoped inside a method

```ruby
def set_greeting
  greeting = "Welcome to the program"
end

set_greeting # call the method to assign the string to the variable called greeting.

puts greeting # Since the variable called greeting was only ever defined as a local variable inside the function, it's not accessible here.
```

#### Solutions for scope

There are two ways to get around this. The first is to pass the data as an argument into the method. The second is to make the variable a global variable so that it's accessible everywhere.

###### Pass in the variable

```ruby
# Initialize the variable
greeting_1 = "Welcome to the program"

# Define the general greet method
def greet_user(greeting, username)
  return greeting + ", " + username + "." # Combines the greeting, a comma and space, the username, and a period to make a full-sentence greeting.
end

# call the function - it's taking two strings as arguments, but one happens to be stored in a variable.
puts greet_user(greeting_1, "Yvette")
```

###### Make the variable global

```ruby
$greeting_1 = "Welcome to the program"

# Define the greet method
def greet_user(username)
  return $greeting_1 + ", " + username + "." # Combines the greeting, a comma and space, the username, and a period to make a full-sentence greeting.
end

# call the function - it's taking one string as an argument, and it will access the greeting separately.
puts greet_user("Yvette")
```

In ruby, we use a dollar sign ($) to make variables global. This means it can be accessed even in the "pocket dimensions" of method bodies.

Both strategies have a lot of utility, and as we examine more complex code, you'll develop an understanding for how and when to use each one most effectively. 
