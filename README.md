# Guided Assignment - Implementing Insertion Sort in C#

## What is Parsing?

In computer programming the term ***Parsing*** is meant to examine a piece of data, and convert it into another form that we can use **Logically**. What exactly does this mean?

Let's take a the following string as an example.
# "12"

Here we have the number "12", but stored as a string. The computer does not understand that it represents a numerical value we can do math with. If we added "12" + "12" we would just end up ***concatenating*** the two strings together, "1212". 

In order for the computer to understand this is a number that we want to perform math with, we need to ***Parse*** it. To do this, we will use a built in command, or ***method***, known as ***.Parse()***.

# New method: *type.Parse(string);*

The .Parse() method takes a string type, and attempts to convert it into a different type, such as a int, double, or bool.

Every type, but string, has a parse that takes a string and try to **Parse** that string into the selected type.

```csharp
public static void Main(string[] args) {

	int intNumber = int.Parse("12"); // Tries to change "12" into 12, and save it as isInteger.

	double doubleNumber = double.Parse("5.23"); // Tries to parse 5.23 into a double
	
	bool trueOrFalse = bool.Parse("true"); // Tries to conver to true or false
	
}
```

Notice the syntax is the same, we need to know
1. What type we want to convert it to.
2. What data, string, we want to pass into it.

If everything works correctly the computer will now treat our value as it's ***Parsed*** type.

```csharp
string string12 = "12"; // 1. Data: A string of "12"
int number12 = int.Parse(string12); //2. Parse: Attemping to Parse our string12
int addValue = number12 + number12; //3. Math: Adding our converted number12 to itself.
Console.WriteLine(addValue); // 4. Display: Result will be 12
```

## Using it with Console.ReadLine();

Since our applications are meant to interact with our user, our ***.Parse()*** is invaluable when working with ***Console.ReadLine()***.

Remember, ***Console.ReadLine()*** ALWAYS returns a string. And we know we can't do math with strings, so that's where our ***Parse()*** comes into play. So if we wanted to user to be able to type in 2 values, and add them, this is what our code will look like.

```csharp
	
	// 1. Getting Data from the user
	Console.Write("Enter your first number: "); // Display asking the user to enter a number
	string userNum1 = Console.ReadLine(); // Getting the users 1st string
	Console.Write("Enter your second number: "); // Display asking the user for their second number
	string userNum2 = Console.ReadLine(); // getting the users 2nd string

	// 2. Parsing the user Data into the correct type
	int number1 = int.Parse(userNum1); // Converting the users 1st string into an int
	int number2 = int.Parse(userNum2); // Converting the users 2nd string into an int

	// 3. Math Operation: Doing some math
	int sum = number1 + number2;

	// 4. Displaying the result
	// Formatting the string to display information correct
	Console.WriteLine($"{number1} + {number2} = {sum}");
```

***Result***
```console
Enter your first number: 24
Enter your second number: 12
24 + 12 = 36
```

We can see why Console.ReadLine() and type.Parse() are so powerful together. Now we are able to convert the users data into a form we can use .

## What if they don't type a number?

The number 1 cause of problems with our code will always be caused by the thing between the chair and the computer, the human. We're prone to typing things in wrong, mis reading, and being distracted. So it's not uncommon to type in the wrong data. What happens when your user types in something that ***isn't*** a number, but you try to parse it. Your program crashes and you get the following error.
### *System.FormatException: 'Input string was not in a correct format.'*

That **Format** being a number. This is very common and we will introduce a way to avoid the in the near future when we look at **try/catch blocks** and the ***.tryParse() method***.

---

## Requirements

1. **Project Setup (10 Points):**
   - Create a console application in C# named `GA_StringParsing_YourName`.

2. **String Parsing Implementation (30 Points):**
   - Implement string parsing using `int.Parse()` and `double.Parse()`, with an explanation in comments.

3. **Handling User Input (20 Points):**
   - Write code to parse user-inputted strings into numbers for average calculation.

4. **Code Clarity and Comments (20 Points):**
   - Ensure the code is clear and well-commented, explaining the parsing process and logic.

5. **Testing and Output Accuracy (15 Points):**
   - Test the code with different inputs and verify the accuracy of the output.

6. **Submission (5 Points):**
   - Upload the complete project to GitHub and provide the repository link.

**Total: 100 Points**


Follow these requirements closely to meet all the criteria outlined in the rubric for your assignment.

---

## Step By Step

### Step 1 - Our first .Parse()

Let's try using our first .Parse. I am also going to give you something known as a ***Try/Catch Block***. This is used to prevent our code from crashing. We will go into more detail later. For now you can just write the following code.

```csharp
// This is an example of how to parse
string myString = "42"; // Enter a number of your choice

try { // try open curly brace
	int myNumber = int.Parse(myString); //1. Parsing our string

	Console.WriteLine($"Your number was an Integral: {myNumber}"); // 2. Displaying our number

} // Closing Curly brace
catch { // catch opening curly brace

	// This will run if our an error is thrown
	Console.WriteLine("You had an error");
} // closing curly brace
```

1. Here we trying to ***Parse*** our string **`myString`** into a number, and save that number into our variable **`myNumber`**.
2. It should work correctly, and will display the following message.

```console
Your number was an Integral: 42
```

---

### Step 2 - Parsing the users number

This time we're going to ask the user to type in 3 numbers, we are then going to display the average of the 3 numbers.

We will do the following
1. Number 1
	1. Ask the user for their first number
	2. Save it as a string with `Console.ReadLine()`
2. Number 2
	1. Ask the user for their second number
	2. Save it as a string with `Console.ReadLine()`
3. Number 3
	1. Ask the user for their third number
	2. Save it as a string with `Console.ReadLine()`
4. Write that try / catch code block like in our first example.
5. This time we are going to do `double.Parse()`, because we going to get the average of the 3 numbers by dividing them. And usually when we divide numbers, we will get decimals.
6. Display the results like `The Average of your 3 numbers is {result}`

```csharp
// This is how parse the users numbers

// Part 1 : Asking the user for the values
// Number 1
Console.Write("Enter your first number: ");
string stringNumber1 = Console.ReadLine();
// Number 2
Console.Write("Enter your second number: ");
string stringNumber2 = Console.ReadLine();
// Number 3
Console.Write("Enter your third number: ");
string stringNumber3 = Console.ReadLine();


try { // try open curly brace
	// Part 2 : Parsing the users values
	double userNumber1 = double.Parse(stringNumber1);
	double userNumber2 = double.Parse(stringNumber2);
	double userNumber3 = double.Parse(stringNumber3);

	// Part 3 : Performing our math
	double sumAllNumbers = userNumber1 + userNumber2 + userNumber3; // Adding our 3 numbers
	double average = sumAllNumbers / 3; // Dividing the sum by the number of elements

	// Part 4 : Displaying our result
	Console.WriteLine($"The average of your 3 numbers is {average}"); 
	
} // Closing Curly brace
catch { // catch opening curly brace

	// This will run if our an error is thrown
	Console.WriteLine("You had an error");
} // closing curly brace
```

*Result*
```console
Enter Your First Number: 23
Enter Your Second Number: 41
Enter Your Third Number: 7
The average of your 3 numbers is 23.666666666666668
```

---
## Final Code

**Goal**: You should be comfortable using the ***Parse()*** method to convert strings to numbers. Keep practicing if you are uncomfortable and soon it'll be second nature when you want to turn a string value or a users input into a number.

Your final code should have all the code from the steps above. Example below.

```csharp
 // This is an example of how to parse
 string myString = "42"; // Enter a number of your choice

 try
 { // try open curly brace
     int myNumber = int.Parse(myString); //1. Parsing our string

     Console.WriteLine($"Your number was an Integral: {myNumber}"); // 2. Displaying our number

 } // Closing Curly brace
 catch
 { // catch opening curly brace

     // This will run if our an error is thrown
     Console.WriteLine("You had an error");
 } // closing curly brace

 // This is how parse the users numbers

 // Part 1 : Asking the user for the values
 // Number 1
 Console.Write("Enter your first number: ");
 string stringNumber1 = Console.ReadLine();
 // Number 2
 Console.Write("Enter your second number: ");
 string stringNumber2 = Console.ReadLine();
 // Number 3
 Console.Write("Enter your third number: ");
 string stringNumber3 = Console.ReadLine();


 try
 { // try open curly brace
   // Part 2 : Parsing the users values
     double userNumber1 = double.Parse(stringNumber1);
     double userNumber2 = double.Parse(stringNumber2);
     double userNumber3 = double.Parse(stringNumber3);

     // Part 3 : Performing our math
     double sumAllNumbers = userNumber1 + userNumber2 + userNumber3; // Adding our 3 numbers
     double average = sumAllNumbers / 3; // Dividing the sum by the number of elements

     // Part 4 : Displaying our result
     Console.WriteLine($"The average of your 3 numbers is {average}");

 } // Closing Curly brace
 catch
 { // catch opening curly brace

     // This will run if our an error is thrown
     Console.WriteLine("You had an error");
 } // closing curly brace

```

---
## Rubric

| Criteria                        | Description                                                                  | Points |
|---------------------------------|------------------------------------------------------------------------------|--------|
| Project Setup                   | Correct creation and naming of the console application.                      | 10     |
| String Parsing Implementation   | Accurate implementation of string parsing with clear, explanatory comments.  | 30     |
| Handling User Input             | Effective parsing of user inputs and calculation of their average.           | 20     |
| Code Clarity and Comments       | Code is easy to understand with comprehensive comments.                      | 20     |
| Testing and Output Accuracy     | Code is thoroughly tested with various inputs, ensuring correct outputs.     | 15     |
| Submission                      | Proper GitHub submission with all necessary files.                           | 5      |
| **Total**                       |                                                                              | 100    |
