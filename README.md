## Crack_Me Solution

https://crackme.s3.amazonaws.com/crack_me_platinum.html

The solution to this coding puzzle involves several steps:

### Look into the logic of triggering the alert and check the critical functions

#### 1. To see the objective, I bypassed the built-in logic to directly display the decoded message. The alert message was obtained by decoding the provided base64 strings:

   ```javascript
   alert(atob("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
   ```
![Objective Image](https://github.com/otammato/crack_me_solution/assets/104728608/2a7669ff-78f0-4a50-a58a-ef593fb4abb7)

#### 2. I separated the direct functions and variables responsible for logic from the secondary ones aimed at the obfuscation and distraction

   The main functions are:

   ```javascript
   // A function to trigger the alert which runs every 2000 milliseconds (2 seconds)
   setInterval(() => {
   
       // Run the "debugger" command (by obfuscating the string "debugger" and then evaluating it)
       ee('dLb'.replace('L', 'e') +'ug' + '14r'.replace('14', 'ge'));
       
       // Check if the "runes" array has more than 2 elements
       // AND if the sum of character codes of the "clue" string is 469
       if (runes.length > 2 && (function (targ) {
                                    tt = 0;
                                    // Calculate the sum of character codes
                                    for (i = 0; i < targ.length; i++) {
                                        tt += targ.charCodeAt(i);
                                    }
                                    // Return true if the sum is 469
                                    return tt == 469;
                                })(clue)){
           // Display an alert saying "Congratulations Oh 1337 One! You have found my treasure!"
           // (By obfuscating the message and then decoding and evaluating it)
           ee(b("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
           
           // Reset the "runes" array to be empty
           runes=[];
       }
   }, 2000);
   
   ```
   <details markdown=1><summary markdown="span">Detailed description for the `setInterval()` function</summary>
     
    
    The `setInterval` function sets up a repeated action to be taken at a fixed interval. In this case, it's set to 2000 milliseconds (or 2 seconds). This means the provided function inside `setInterval` will execute every 2 seconds.
    
    #### a. `ee('dLb'.replace('L', 'e') +'ug' + '14r'.replace('14', 'ge'));`
    This line is obfuscating a string:
    
    - `'dLb'.replace('L', 'e')` results in the string "deb".
    - `'ug'` is just the string "ug".
    - `'14r'.replace('14', 'ge')` results in the string "ger".
    
    So, the final concatenated string is "debugger". This means the line translates to `ee("debugger")`. I also found out that `ee` is an alias for the `eval` function, this is a command to execute the "debugger" statement, which will pause execution in debugging tools like the Chrome DevTools.
    
    #### b. The `if` statement:
    
    This checks two conditions:
    
    i. `runes.length > 2`: This checks if the `runes` array has more than 2 elements.
    
    ii. `(function (targ) {...})(clue)`: This is an immediately-invoked function expression (IIFE). It receives `clue` as its argument (named `targ` inside the function). The function calculates the sum of the Unicode character codes of `targ` and checks if the sum equals 469.
    
    If both conditions are true, then:
    
    - The obfuscated string `b("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik=")` is decoded using function `b` (which is a variable for `atob`, responsible for decoding base64 strings) and then evaluated using `ee` (which is `eval`). The decoded string is: `alert("Congratulations Oh 1337 One! You have found my treasure!")`, which will show an alert box with this congratulatory message.
    
    - The `runes` array is reset to be empty with `runes=[]`.
    
    In summary, every 2 seconds, this script triggers a debugger, checks if certain conditions are met, and if they are, alerts the user that they've found a "treasure".
   </details>


<details markdown=1><summary markdown="span">Old</summary>

### Crack_Me Solution

https://crackme.s3.amazonaws.com/crack_me_platinum.html

The solution to this coding puzzle involves several steps:

#### 1. Displaying the Objective Message:
To get an overview of the task at hand, I manipulated the code to bypass the built-in logic and directly display the decoded message. The alert message was obtained by decoding the provided base64 strings:

```javascript
alert(atob("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
```

![Objective Image](https://github.com/otammato/crack_me_solution/assets/104728608/2a7669ff-78f0-4a50-a58a-ef593fb4abb7)

#### 2. Understanding the Alert Mechanism:
Upon further examination, I discerned the mechanism triggering the alert:

- The `setInterval()` function's `if` condition performs two checks:
  - The length of the `runes` array must exceed 2.
  - The sum of ASCII values of characters in the clue string must be equal to 469. I modified `tt == 469;` into `tt >= 469;` for the simplicity to trigger `setInterval()` function
  
If these conditions are met, the encoded congratulatory message displays:

```javascript
ee(b("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
```

This message translates to:
```
alert("Congratulations Oh 1337 One! You have found my treasure!")
```

#### 3. Disabling debugger Mechanism:
A mechanism in the `setInterval()` function launches the debugger every 2 seconds to halt the code execution if DevTools are open. To bypass this, I disabled the function:

```javascript
// ee('dLb'.replace('L', 'e') +'ug' + '14r'.replace('14', 'ge'));
```

#### 4. Disabling Image ID Manipulation:
The code manipulates the `clue` variable based on the Image's ID. I disabled this mechanism to simplify the process:

```javascript
/* 
// var el = new Image();
// Object.defineProperty(el, 'id', {
// get: function () {
// clue = b(tY(spikes[0x05]));
// }
// });         
// requestAnimationFrame(function check() {
// console.dir(el);
// console.clear();
// requestAnimationFrame(check);
// });
*/
```

#### 5. Displaying Coordinates:
For convenience, I modified the IChing() function to display x and y coordinates in a standard format instead of the base64 encoded string:

```javascript
document.getElementById("gps").innerHTML = y.toString() + "," + x.toString();
```

#### 6. Retrieving the Clue:
Using DevTools and the `clue` command in the console, I identified the keyword 'LAMBERT'. 

```javascript
clue
// Outputs: 'LAMBERT'
```

The ASCII values for the characters in `LAMBERT` are:

- L: 76
- A: 65
- M: 77
- B: 66
- E: 69
- R: 82
- T: 84

#### 7. Solving Using Coordinates:
I then matched the ASCII values to the coordinates on the screen:

- Drag "X" to (x: 65, y: 76) for 'A' and 'L'.
  ```javascript
  runes
  // Outputs: ['alpha']
  ```

- Move "X" to (x: 66, y: 77) for 'B' and 'M'.
  ```javascript
  runes
  // Outputs: ['alpha', 'beta']
  ```

- Next, to (x: 82, y: 69) for 'R' and 'E'.
  ```javascript
  runes
  // Outputs: ['alpha', 'beta', 'gamma']
  ```

- The final position, (x: 0, y: 84), wasn't necessary. With the length of `runes` array > 2 and the sum of ASCII values of `LAMBERT` > 469, the `setInterval()` function successfully triggers the alert:

![Solution Image](https://github.com/otammato/crack_me_solution/assets/104728608/9c30ed14-b0cb-4034-866f-6de9f55e849d)

<br>

---

<br>

The modified file is available here:

[https://github.com/otammato/crack_me_solution/blob/da85f213666ba2357f582e569ee83f354b6a0b44/crack_me_platinum.html](https://otammato.github.io/crack_me_solution/crack_me_platinum.html)https://otammato.github.io/crack_me_solution/crack_me_platinum.html

Instructions to test it:

1. Type the `clue` in the console and hit the enter to make sure the clue is 'LAMBERT'
2. Drag the "X" marker (canary) around the screen and hit the target coordinates
3. As you move the marker, the coordinates of the marker will be displayed by the IChing function.
4. Moving the marker to specific coordinates triggers checks against the ASCII values of the clue variable.
5. When the correct set of coordinates is hit in sequence, an alert should display the treasure message.


<img width="1000" alt="Screenshot 2023-09-10 at 23 37 22" src="https://github.com/otammato/crack_me_solution/assets/104728608/48460c81-3f72-4029-a71f-ffb1c0884d00">


</details>
