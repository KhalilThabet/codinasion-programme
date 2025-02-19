---
title: Number to Strings
description: Write a program to convert number to strings
image: hero.png
tags:
  - python
  - c
  - cpp
  - java
  - js
  - cs
  - go
contributors:
  - aryangupta701
  - NeelPatel31
  - seraph776
  - Parthan-Sachin
  - hansleykowlessur
  - umaxyon
---

## Write a program to convert number to strings

```txt
Input  : 51
Output : five one
```

---

<CodeBlock>

```python
def numbers_to_strings(n: int) -> str:
    """Converts numbers to string"""
    d = {0: 'zero', 1: 'one', 2: 'two', 3: 'three', 4: 'four',
         5: 'five', 6: 'six', 7: 'seven', 8: 'eight', 9: 'nine'}
    n = [int(i) for i in str(n)]
    output = ' '.join([d.get(i) for i in n])

    return output


if __name__ == '__main__':
    print(numbers_to_strings(776))  # seven seven six
```

```c
#include <stdio.h>
#include <math.h>

int main()
{
    int n, num = 0, digits;

    printf("Enter any number to print in words: ");
    scanf("%d", &n);

    digits = (int)log10(n);

    while (n != 0)
    {
        num = (num * 10) + (n % 10);
        n /= 10;
    }
    digits = digits - ((int)log10(num));

    while (num != 0)
    {
        switch (num % 10)
        {
        case 0:
            printf("Zero ");
            break;
        case 1:
            printf("One ");
            break;
        case 2:
            printf("Two ");
            break;
        case 3:
            printf("Three ");
            break;
        case 4:
            printf("Four ");
            break;
        case 5:
            printf("Five ");
            break;
        case 6:
            printf("Six ");
            break;
        case 7:
            printf("Seven ");
            break;
        case 8:
            printf("Eight ");
            break;
        case 9:
            printf("Nine ");
            break;
        }
        num /= 10;
    }
    while (digits)
    {
        printf("Zero ");
        digits--;
    }

    return 0;
}
```

```cpp
#include <iostream>
#include <string>
using namespace std;
int main()
{
    int a, n = 0;
    string word[] = {"Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"};
    cout << "Input  : ";
    cin >> a;
    string op = "";
    while (a > 0)
    {
        n = a % 10;
        op.insert(0, word[n]);
        op.insert(0, " ");
        a = a / 10;
    }
    cout << "Output :" << op << endl;
    return 0;
}
```

```java
import java.util.Scanner;

public class numbers_to_string {
    public static void main(String[] args) {
        String[] word = { "Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine" };
        Scanner sc = new Scanner(System.in);
        System.out.print("Input  : ");
        String a = sc.nextLine();
        System.out.print("Output : ");
        for (int i = 0; i < a.length(); i++) {
            System.out.print(word[(int) a.charAt(i) - 48] + " ");
        }
        System.out.println();
        sc.close();
    }
}
```

```javascript
const words = [
  "Zero",
  "One",
  "Two",
  "Three",
  "Four",
  "Five",
  "Six",
  "Seven",
  "Eight",
  "Nine",
];

convert(12223455);

function convert(input) {
  if (typeof input != "number") return console.error("Not a number");
  console.log("Input  :", input);

  var inp = input.toString();

  let arr = [];

  for (let i = 0; i < inp.length; i++) {
    if (inp[i] === ".") arr.push("point");
    else arr.push(words[inp[i]]);
  }

  console.log("Output :", ...arr);
}
```

```cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace Number_to_Strings
{
    class NumberToStrings
    {
        static void Main(string[] args)
        {
            try
            {
                // Initialisation
                string numStr = string.Empty;

                // Contains the mapping of numeric value to their string equivalent
                IDictionary<int, string> dicNumToStr =
                    new Dictionary<int, string>()
                    {
                        { 0, "zero" },
                        { 1, "one" },
                        { 2, "two" },
                        { 3, "three" },
                        { 4, "four" },
                        { 5, "five" },
                        { 6, "six" },
                        { 7, "seven" },
                        { 8, "eight" },
                        { 9, "nine" }
                    };

                // Read value from keyboard
                Console.Write("Input  : ");
                numStr = Console.ReadLine();
                Console.WriteLine();

                // Convert to List of integer
                // ===========================
                List<int> arrOfNumericValues =
                    numStr
                        .ToCharArray() // <= Convert string to array of char. E.g. "123" => ['1','2','3']
                        .ToList() // <= Convert array to List in order to use Linq to be able to convert each char to integer
                        .ConvertAll(// 1. Convert each char to string. E.g. '1' => "1"
                        // 2. Convert each string to integer. E.g. "1" => 1
                        eachChar => int.Parse(eachChar.ToString()));

                // Convert numbers to string
                // =========================
                string resultStr =
                    string
                        .Join(" ", // <= White space separator
                        arrOfNumericValues
                            .Select(// Map each number against their respective value in the dictionary. E.g. 1 => "one"
                            eachNumber => dicNumToStr[eachNumber]));

                // Display result
                Console.WriteLine($"output : {resultStr}");
            }
            // Handle other exceptions
            catch (Exception ex)
            {
                Console.WriteLine($"Errors => {ex.Message}{Environment.NewLine}{ex.StackTrace}");
            }
        }
    }
}
```

```go
package main

import (
	"fmt"
	"regexp"
)

var NumStrList = []string{"zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"}

func main() {
	var str string

	fmt.Print("Input Number : ")
	fmt.Scan(&str)

	isNum, err := regexp.MatchString("^\\d+$", str)
	if err != nil || !isNum {
		fmt.Printf("Input error: %s", str)
		return
	}

	fmt.Print("\nOutput : ")
	for i := 0; i < len(str); i++ {
		fmt.Printf("%s ", NumStrList[str[i]-48]) // ascii code 48 -> 0
	}
	fmt.Println()
}
```

</CodeBlock>
