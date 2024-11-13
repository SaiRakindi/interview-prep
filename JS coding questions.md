# JS coding questions

Created: November 13, 2024 9:02 PM

Here are JavaScript solutions to each of the problems you listed, written without using built-in functions:

### 1. Program to find longest word in a given sentence ?

```jsx
function findLongestWord(sentence) {
    let words = sentence.split(" ");
    let longestWord = "";

    for (let i = 0; i < words.length; i++) {
        if (words[i].length > longestWord.length) {
            longestWord = words[i];
        }
    }

    return longestWord;
}

```

### 2. How to check whether a string is palindrome or not?

```jsx
function isPalindrome(str) {
    let len = str.length;
    for (let i = 0; i < len / 2; i++) {
        if (str[i] !== str[len - 1 - i]) {
            return false;
        }
    }
    return true;
}

```

### 3. Write a program to remove duplicates from an array ?

```jsx
function removeDuplicates(arr) {
    let uniqueArr = [];
    for (let i = 0; i < arr.length; i++) {
        let isDuplicate = false;
        for (let j = 0; j < uniqueArr.length; j++) {
            if (arr[i] === uniqueArr[j]) {
                isDuplicate = true;
                break;
            }
        }
        if (!isDuplicate) {
            uniqueArr.push(arr[i]);
        }
    }
    return uniqueArr;
}

```

### 4. Program to find Reverse of a string without using built-in method ?

```jsx
function reverseString(str) {
    let reversed = "";
    for (let i = str.length - 1; i >= 0; i--) {
        reversed += str[i];
    }
    return reversed;
}

```

### 5. Find the max count of consecutive 1’s in an array ?

```jsx
function maxConsecutiveOnes(arr) {
    let maxCount = 0;
    let currentCount = 0;

    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === 1) {
            currentCount++;
            if (currentCount > maxCount) {
                maxCount = currentCount;
            }
        } else {
            currentCount = 0;
        }
    }

    return maxCount;
}

```

### 6. Find the factorial of given number ?

```jsx
function factorial(num) {
    if (num === 0 || num === 1) return 1;
    let result = 1;
    for (let i = 2; i <= num; i++) {
        result *= i;
    }
    return result;
}

```

### 7. Given 2 arrays that are sorted [0,3,4,31] and [4,6,30]. Merge them and sort [0,3,4,4,6,30,31] ?

```jsx
function mergeAndSort(arr1, arr2) {
    let mergedArr = [];
    let i = 0, j = 0;

    while (i < arr1.length && j < arr2.length) {
        if (arr1[i] < arr2[j]) {
            mergedArr.push(arr1[i]);
            i++;
        } else {
            mergedArr.push(arr2[j]);
            j++;
        }
    }

    while (i < arr1.length) mergedArr.push(arr1[i++]);
    while (j < arr2.length) mergedArr.push(arr2[j++]);

    return mergedArr;
}

```

### 8. Create a function which will accepts two arrays arr1 and arr2. The function should return true if every value in arr1 has its corresponding value squared in array2. The frequency of values must be same.

```jsx
function hasSquaredCounterparts(arr1, arr2) {
    if (arr1.length !== arr2.length) return false;

    for (let i = 0; i < arr1.length; i++) {
        let value = arr1[i] * arr1[i];
        let found = false;
        for (let j = 0; j < arr2.length; j++) {
            if (arr2[j] === value) {
                arr2[j] = null; // Mark as checked
                found = true;
                break;
            }
        }
        if (!found) return false;
    }
    return true;
}

```

### 9. Given two strings. Find if one string can be formed by rearranging the letters of other string.

```jsx
function areAnagrams(str1, str2) {
    if (str1.length !== str2.length) return false;

    let charCount1 = {}, charCount2 = {};
    for (let i = 0; i < str1.length; i++) {
        charCount1[str1[i]] = (charCount1[str1[i]] || 0) + 1;
        charCount2[str2[i]] = (charCount2[str2[i]] || 0) + 1;
    }

    for (let char in charCount1) {
        if (charCount1[char] !== charCount2[char]) return false;
    }
    return true;
}

```

### 10. Write logic to get unique objects from below array ?

I/P: [{name: "sai"},{name:"Nang"},{name: "sai"},{name:"Nang"},{name: "111111"}];

O/P: [{name: "sai"},{name:"Nang"}{name: "111111"}

```jsx
function uniqueObjects(arr) {
    let uniqueArr = [];
    for (let i = 0; i < arr.length; i++) {
        let isDuplicate = false;
        for (let j = 0; j < uniqueArr.length; j++) {
            if (arr[i].name === uniqueArr[j].name) {
                isDuplicate = true;
                break;
            }
        }
        if (!isDuplicate) uniqueArr.push(arr[i]);
    }
    return uniqueArr;
}

```

### 11. Write a JavaScript program to find the maximum number in an array.

```jsx
function findMax(arr) {
    let max = arr[0];
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > max) max = arr[i];
    }
    return max;
}

```

### 12. Write a JavaScript function that takes an array of numbers and returns a new array with only the even numbers.

```jsx
function filterEvenNumbers(arr) {
    let evenNumbers = [];
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] % 2 === 0) evenNumbers.push(arr[i]);
    }
    return evenNumbers;
}

```

### 13. Write a JavaScript function to check if a given number is prime.

```jsx
function isPrime(num) {
    if (num < 2) return false;
    for (let i = 2; i < num; i++) {
        if (num % i === 0) return false;
    }
    return true;
}

```

### 14. Write a JavaScript program to find the largest element in a nested array.

[[3, 4, 58], [709, 8, 9, [10, 11]], [111, 2]]

```jsx
function findLargestInNested(arr) {
    let largest = -Infinity;

    function findMaxInArray(subArray) {
        for (let i = 0; i < subArray.length; i++) {
            if (Array.isArray(subArray[i])) {
                findMaxInArray(subArray[i]);
            } else {
                if (subArray[i] > largest) largest = subArray[i];
            }
        }
    }

    findMaxInArray(arr);
    return largest;
}

```

### 15. Write a JavaScript function that returns the Fibonacci sequence up to a given number of terms.

```jsx
function fibonacci(n) {
    let fib = [0, 1];
    for (let i = 2; i < n; i++) {
        fib[i] = fib[i - 1] + fib[i - 2];
    }
    return fib.slice(0, n);
}

```

### 16. Given a string, write a javascript function to count the occurrences of each character in the string.

```jsx
function countCharacters(str) {
    let counts = {};
    for (let i = 0; i < str.length; i++) {
        let char = str[i];
        counts[char] = (counts[char] || 0) + 1;
    }
    return counts;
}

```

### 17. Write a javascript function that sorts an array of numbers in ascending order.

```jsx
function sortAscending(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[i] > arr[j]) {
                let temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}

```

### 18. Write a javascript function that sorts an array of numbers in descending order.

```jsx
function sortDescending(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[i] < arr[j]) {
                let temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}

```

### 19. Write a javascript function that reverses the order of words in a sentence without using the built-in reverse() method.

```jsx
function reverseWords(sentence) {
    let words = [];
    let word = "";
    for (let i = 0; i < sentence.length; i++) {
        if (sentence[i] === " ") {
            if (word) {
                words.unshift(word);
                word = "";
            }
        } else {
            word += sentence[i];
        }
    }
    if (word) words.unshift(word);

    return words.join(" ");
}

```

### 20. Implement a javascript function that flattens a nested array into a single-dimensional array.

```jsx
function flattenArray(arr) {
    let flat = [];
    function flatten(subArray) {
        for (let i = 0; i < subArray.length; i++) {
            if (Array.isArray(subArray[i])) {
                flatten(subArray[i]);
            } else {
                flat.push(subArray[i]);
            }
        }
    }

    flatten(arr);
    return flat;
}

```

### 21. Write a function which converts string input into an object

("a.b.c", "someValue");

{a: {b: {c: "someValue"}}}

```jsx
function stringToObject(str, value) {
    let parts = str.split(".");
    let result = {};
    let current = result;

    for (let i = 0; i < parts.length; i++) {
        if (i === parts.length - 1) {
            current[parts[i]] = value;
        } else {
            current[parts[i]] = {};
            current = current[parts[i]];
        }
    }

    return result;
}

```

These solutions avoid using JavaScript's built-in functions, relying on core programming concepts to achieve each task.