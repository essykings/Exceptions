# Handling exceptions in Python
This tutorial will provide an introduction to python exceptions, types of exceptions and how to raise and handle errors in python.

## What is a python exception?
A python exception is an error that occurs when executing a program, causing the program to stop. 

## Handling Exceptions
In the example below, we prompt the user to enter a number and after execution, the program gives out the value of the number squared.  The program will work as long as you enter a number as input.

#### Example

    squared = True

    while squared:
      x = int(input("Please enter a number: "))
      print('%s squared  is  %s' % (x, x**2))

When you enter a string or any other character that is not a number, for example, ```one``` , the program will raise a Value Error exception as shown below


    ValueError: invalid literal for int() with base 10: 'one'

This is where handling exceptions comes in.You need to know how to properly handle exceptions, especially in production because if they are not handled, your program won't know what to do.

Let's see how we can handle the above error. This is done by surrounding the program that you think will cause an error with a ``try``keyword and matching it with an ``except`` keyword to handle the exception.

Let's rewrite the same program and this time take care of any exceptions that may arise.

    squared = True

    while squared:
        try:
            x = int(input("Please enter a number: "))
            print('%s squared  is  %s' % (x, x**2))
        except ValueError:
            print("Please enter a valid number")

As you can see from the above program, the code inside the ``try`` statement is executed first. If no error occurs,  the rest of the code is executed and the ``except`` statement is skipped.

In the event that an exception is raised, the program executes the ``except`` statement that matches it's ``try`` statement followed the rest of the code outside of the ``try except`` block if any.

##Types of Exceptions in Python
Python has several built-in exceptions. Let’s take a glance at some of them so that you can get a perspective of what they are and how to use them.

###Key Error
This is an error that occurs when a dictionary is passed and one of the keys is not present in the dictionary.
The following is a Django view used to authenticate users and it expects a dictionary of username and password. If any of the keys is not passed in the input, the program raises a key error exception.

    


    def authenticate_user(request):
    try:
        email = request.data['username']
        password = request.data['password']

        user = authenticate(email=email, password=password)

        if user and user.is_active:
            return Response(user_details,status=HTTP_200_OK)
        else:
            res = {'error': 'can not authenticate with the given credentials'}
            return Response(res, status=status.HTTP_400_BAD_REQUEST)
    except KeyError:
    res = {'error': 'please provide a username and a password'}

### IndentationError Exception

This kind of exception is raised when the indentation of code is not properly specified.
Let's write a function that checks if a number # is even.

    def is_even(number):

        if number % 2 == 0 and number != 0:
        print(" %s is an even number" % (number))
        else:
        print('%s  is an Odd number' % (number))


The function will result in an indentation error on both lines 2 and 4 because it expects the code to be indented with 4 spaces 

If you execute the program, it will give the following output.
 
    IndentationError: expected an indented block


### Invalid syntax Exception
This is the most common type of exception in python. It occurs when there is an error in the python syntax.
Let's look at the example below


    def even(n):
      if n/2 ==0:
        print(it’s even)
      else:
        print("not even")
        
    print(even(7))



The output of this code will result in an invalid syntax at line 3 because the string ``it's even``  is not enclosed in quotes

####Output
 
 
    Traceback (most recent call last):
      File "python", line 3
        print(its even)
                   ^
    SyntaxError: invalid syntax


###TypeError
This exception is raised when an operation or function is attempted that is invalid for the specified data type.
In the example below, the function ``sum_of_numbers`` takes in 2 arguments and adds them together
When you attempt to call the function with 3 arguments, it raises a TypeError exception because it expects only 2arguments.

    def sum_of_numbers(a, b):
        return a + b

    print(sum_of_numbers(1,2,7))

#### output

    TypeError: total() takes 2 positional arguments but 3 were given

##The try/catch, else and finally clauses.
There are several other components of exceptions and that is the else and finally clauses.
We have already been able to use try and catch statements which are used to catch errors. Let's now look at the else and finally statements.

###The Else Clause
The else clause is used to execute code when the program does not raise an exception.
Consider the example we used in the beginning of this tutorial, we are going to execute the print statement inside the else statement.

    squared = True
    while squared:
        try:
            x = int(input("Please enter a number: "))

        except ValueError:
            print("Please enter a valid number")
        else:
            print('%s squared  is  %s' % (x, x**2))

##The try/catch, else and finally clauses.
The try … except statement has other optional clauses, the else and finally clauses.
We have already been able to use try and catch statements which are used to catch errors. Let's now look at the else and finally clauses.

###The Else Clause
The else clause is used to execute code when the program does not raise an exception. It is also better to use the else clause than adding additional code to the try clause, this is because it avoids unintentionally catching an exception that wasn’t raised by the code being protected by the try... except statement.
Consider the example we used in the beginning of this tutorial, we are going to execute the print statement inside the else statement as shown below.

    squared = True

    while squared:
        try:
            x = int(input("Please enter a number: "))

        except ValueError:
            print("Please enter a valid number")
        else:
            print('%s squared  is  %s' % (x, x**2))

###The Finally clause

This clause is meant to define clean-up actions that must be performed under all circumstances.
A finally clause if used must always be executed before leaving the statement try, whether an exception has occurred or not.

Let's include the finally clause in our example.

    squared = True

    while squared:
      try:
        x = int(input("Please enter a number: "))
      except ValueError:
        print("Please enter a valid number")
      else:
       print('%s squared  is  %s' % (x, x**2))
      finally:
        print("completed")

    #result

    # Please enter a number:  100
    # 100 squared  is  10000
    # completed
    # Please enter a number:  
      
      
## Conclusion
I hope this tutorial has cleared out any confusion you had on Python Exceptions. 
**Note:**   Please keep in mind that a ```try``` clause will only handle its corresponding ``except `` clause even if there are multiple except clauses handlers.


You can find more material on the Python [documentation](https://docs.) 
