# **Array Basics**

An `array` is simply a list of values.
- When working with a large dataset, you may not know how many variables you need to store, or you may know, but the number may be huge.
- To write an array in JS, use square brackets `[]` and a comma `'` to separate each value.
- You can put anything inside of an array: 
    - numbers (primes)
    - strings (names)
    - booleans (booleans)
    - combinations of all primatives (mixedTypes)
    - Even other arrays inside of an array.

- You could write out the variables individually: 
    - let firstNum = 3;
    - let secondNum = 5;
    - let thirdNum = 112;
    - let FourthNum = -2;

- OR write it out as an array:
    - let nums = [3, 5, 112, -2];
    - Wow, look at how much time I saved.

![alt text](<Screenshot 2024-03-09 at 10.34.56 AM.png>)

**Accessing, updating, adding, and removing from array values**

- To access an element, specify the name of array followed by square brackets and the position (index) of the element.
    - Arrays are zero-indexed, meaning the first element is 0 instead of 1.

![alt text](<Screenshot 2024-03-09 at 11.07.36 AM.png>)

- To `Update` a value, assign an element at an index to a new value.
    - let nums = [3, 5, 112, -2];
    - nums[0] = 33;
    - nums[3] = 2;
    - arr; should now equal [33, 5, 112, 2]

- To `Add` to an array, there are several methods.  
    - 1. Set a new value at a new index within array.
      - let nums = [3, 5, 112, -2];
      - nums[4] = 88;
      - arr; should equal [3, 5, 112, -2, 88];
    - 1.1. Be careful, you can add an element at any index, but if you skip an index it will be filled with undefined values.
        - let nums = [3, 5, 112, -2];
      - nums[6] = 88;
      - arr; should equal [3, 5, 112, -2, undefined, undefined, 88];
    - 2. Use the `push` function to add to the end of the array, it will then return the `length` of the array. (length ignores the zero-index quality and returns how many actual number of elements)
        - let nums = [3, 5, 112, -2];
        - nums.push(88); will return with the length of "5" elements and make the new nums array be nums = [3, 5, 112, -2, 88];
    - 2.1. `unshift` is a similar function, but adds an element at the beginning of the array (index 0"). 
         - let nums = [3, 5, 112, -2, 88];
        - nums.unshift(-21); will return with the length of "6" elements and make the new nums array be nums = [-21, 3, 5, 112, -2, 88];
- To `Remove` elements from an Array there are 2 methods.
    1. Uncommon method is to manually set the length of the array to a smaller number.
        - let nums = [3, 5, 112, -2, 88];
        - nums.length = 2; //returns new length
        - nums; // [-21,3]
    2. A more common apporach is the `pop()` function. This works like the opposite of `push` by removing items from the back of the array. However, `pop()` doesnt return the new length, it returns value just removed.
        - let nums = [3, 5, 112, -2, 88];
        - nums.pop(); // returns "88"
        - nums; [3, 5, 112, -2]
    3. If you want to remove an element from the front of an array, use `shift()`. Exactly the opposite of `unshift`. Similar to pop(), shift() returns the removed value, not the new length.
        - nums.shift() // returns "3"
    4. You can use the `delete` command to remove a value at a specified index. This does not delete the value, it replaces it with undefined. Rarely used outside of `objects`.

**Removing, Adding, or Both with `Splice`**
- When you use the splice() command, whatever you put the index positions inside of the parenthesis effects the output.
- The first position (aka argument) splice(1, 0, 0, 0) assigns the working index position.
 - The second position (argument) is the ending index.
 - ex, let nums = [1,2,3,4]; 
    - nums.splice(0,1); //returns [1] and nums; // [2,3,4]
    
- Building off of this, the third position will replace whatever you removed at the first position.
    - nums.splice(0,1,7); //returns [1] and nums; will returns // [7,2,3,4]
- You can also insert more values at new index positions by specifying the starting index positions at the first argument, the ending index position at the second argument, then new values in the following arguements.  // If you only want to change one position in the array (ex, just "b" in the example below) let the second argument be one index position less that the first argument (ex, arr.splice(1,0,"x","y","z"))
![alt text](<Screenshot 2024-03-12 at 2.17.56 PM.png>)

## **Array Methods**

**Common array functions and properties**

- *Length* - returns how many elements in an array.
    - let nums = [0,1,2,3,4]
    - nums.length; // 5
    - You can access the last element in an array of unknown length by using `nums[nums.length-1];`
- *Slice* - makes a copy of an array. Can copy an entire array or make a copy of a subarray. `slice()`
    - let nums = [0,1,2,3,4]
    - let copy = nums.slice();
    - copy; // [0,1,2,3,4];
- OR you can input 2 arguments into slice. The first argument indicates the starting index and the second argument indicates the ending index. the resulting subarray consists of all values from the starting index to (but NOT including) the ending index.
![alt text](<Screenshot 2024-03-14 at 11.53.15 AM.png>)

* *Concat* - Joins 2 arrays together. You can concact multiple arrays together and it will return a single array to you.
    - Let arr1 = [1,2,3];
    - Let arr2 = [4,5,6];
    - let arr3 = arr1.concat(arr2); // arr3; will = [1,2,3,4,5,6]
    - Multiple - let arr123 = arr.1.concact(arr2,arr3); // [1,2,3,4,5,6,1,2,3,4,5,6]
    - Lastly you can add a comma-separated list of values to be concactenated into into an existing array.
        -let newArr = arr1.concact(x,y,z);
    ![alt text](<Screenshot 2024-03-18 at 11.45.05 AM.png>)
* *Join* - joins elements of an array into a string. This string is seperated by whatever you pass in as an argument to join. This argument is referred to as a delimiter.
    - let arr4 = ["Hello", "World"];
    - arr4.join(""); // "Hello World"
    - OR let arr5 = ["Good", "Morning", "World"];
    - arr5.join(!") + "!"; // "Good! Morning! World!"
* *indexOf* - returns the index position of the entered value. If no value is found, it reurns -1.
    - let arrA = [8,6,9,12,1,8,8];
    - arrA.indexOf(9); // 2
    - arrAindexOf(8);// 0 (stops at first index read L>R).
    - This function commonly used to check if an element is in an array. See ex below.

![alt text](<Screenshot 2024-03-18 at 12.39.36 PM.png>)

* *lastIndexOf - works the same as indexOf, but starts at the end of the array (reads R>L). Still returns -1 if no such value exists.
    - let arrA = [8,6,9,12,1,8,8];
    - arrA.lastIndexOf(8); //6.

* *includes* - This function returns true/false to see if a value is in an array. ex, arr1.includes(); //true/false

* *Reference vs Value* - A distinction between primitives and objects (arrays are a type of object in JS) is how their values are passed when assigned to new variables.
- ex ![alt text](<Screenshot 2024-03-18 at 2.15.46 PM.png>)
    - In this ex, by changing the second variable, it did not affect the first variable. This is due to each primitive type having a specific address in memory. In this case JS created a copy of the "Elie" string and assigned that value to the second variable, allowing **two variables to store identical looking strings, and them being able to be modified independently of each other**

    * ex2
    ![alt text](<Screenshot 2024-03-18 at 2.19.56 PM.png>)

        * in ex2, The original array was changed when a new element was pushed into the copy. By using `===` both variable names refer to the same array.
        [Further Reading](https://stackoverflow.com/questions/6605640/javascript-by-reference-vs-by-value)

### **Array Iteration**

Simply put, iteration is looping. Iteration makes it way through an array and does something with each element. It is much more efficient than manually making changes, especially in large arrays.

* **For loops**
    - A For loop consists of 3 parts followed by a block of code within {}.
    - for (initializer; condition; counter){}
        - initializer - declare variables to be used in loop. Usually declare a variable called `i` which *serves as a counter variable for the number of times we should loop.*
        - condition - Must be an expression that returns true/false. aka keep running loop as long as condition is true.
        - counter - this is how we change variables initialized (increase/decrease)
        - *As long as the condition is true, the code inside {} will run, after running the counter expression runs, then the condition will be checked again.*

        - **You can use a loop to iterate through an array. i refers to the  current index in the array, the condition tells the loop to continue until i = length of the array, and the counter increments i.**

    ex, here are 2 ways you could round out integers in an array. let decimals = [1.1, 1.6, 2.8, 0.4, 3.5, 1.6];

    manually -![alt text](<Screenshot 2024-03-21 at 1.16.50 PM.png>)
    iteration -![alt text](<Screenshot 2024-03-21 at 1.17.14 PM.png>)

* **While loops**
    * Similar to a for loop, but while loops only need a condition. You handle initialization before the loop, handle increment/decrement inside the loop (if you do not increment/decrement inside loop, it will never terminate and result in an infinite loop).
    ![alt text](<Screenshot 2024-03-21 at 1.26.53 PM.png>)
        - to continue decimal example, ![alt text](<Screenshot 2024-03-21 at 1.37.10 PM.png>)

* **Do While loops**
    * Similar to while loops, do...while loops specify the condition at the end.
    * The main difference between a while loop and a do..while loop is that the code within a do...while loop is executed at least once.
    ![alt text](<Screenshot 2024-03-21 at 4.18.25 PM.png>)

* **Exiting outta loops**
If you want to exit a loop before it has finished, use `break`.
![](<Screenshot 2024-03-22 at 12.38.24 PM.png>)

* You can also skip thr current iteration and continue the loop at the next step in the iteration by using `continue`
![](<Screenshot 2024-03-22 at 12.40.47 PM.png>)

* **for...of loop**
JavaScript recently released a new simpler loop to iterate with less code.
* A `for...of` loop iterates over an array and assigns a variable to each element in the array. (*be sure to declare the variable with `let`) 
![alt text](<Screenshot 2024-03-22 at 12.47.11 PM.png>)

* **Strings, revisited**
Strings and arrays are slightly similar datatypes, but have major differences. You can also iterate over strings (and objects) 
![alt text](<Screenshot 2024-03-22 at 1.02.37 PM.png>)
* OR
![alt text](<Screenshot 2024-03-22 at 1.24.03 PM.png>)

* **Split** - is used whe you need to turn a string into an array. The split method turns a string into an array. To split a string into an array you can use the split method and pass in a delimiter value (*A delimiter is a sequence of one or more characters that specifies the start and end of two separate parts of text*)

![alt text](<Screenshot 2024-03-22 at 1.32.11 PM.png>)
* If you pass a delimiter into the () of split method, the delimiting values will be removed from the array.
![alt text](<Screenshot 2024-03-22 at 1.41.31 PM.png>)
* You can then turn the array back into a string with the `join` method. **split does the oposite of join**
![alt text](<Screenshot 2024-03-22 at 1.47.18 PM.png>)
Another example:
![alt text](<Screenshot 2024-03-22 at 1.51.18 PM.png>)

* **Mutability** - You can update any array value by accessing an array element and assigning it a new value.
- ex, let arr = ["hi", "bye"];
arr[0] = "howdy"; arr; //["howdy, "bye"]
* You can also access characters within strings using []s. However, unlike with arrays, you cannot reassign the value of a character in a string. See below.

![alt text](<Screenshot 2024-03-22 at 2.06.01 PM.png>)
* This istinction highlights a concept called "mutability". Arrays in JS are mutable (you can easily change any element within an array with a reassignment).
* However, strings are *immutable*, you cannot change the characters within. Any operation that does change the charcters within produces a new string (instead of mutating the original string).

#### **Array Excercises**
![alt text](<Screenshot 2024-03-22 at 2.49.06 PM.png>)
