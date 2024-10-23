### JavaScript Essentials

---

#### Iterating over Data Structures:
- **Can iterate over:** arrays, sets, maps, and strings.
- **Cannot iterate over:** objects directly.

---

### Spread Operator

- **For Arrays:**
  ```js
  [...arr]
  ```

- **For Objects:**
  ```js
  const newRestaurant = { foundedIn: 1998, ...restaurant, founder: 'Guiseppe' };
  ```

---

### Rest Operator

```js
const add = function (...numbers) {
  let sum = 0;
  for (let i = 0; i < numbers.length; i++) sum += numbers[i];
  console.log(sum);
};

add(2, 3);             // 5
add(5, 3, 7, 2);       // 17
add(8, 2, 5, 3, 2, 1); // 21
```

---

### Short Circuiting (&& and ||)

- **Ternary Operator:**
  ```js
  const guests1 = restaurant.numGuests ? restaurant.numGuests : 10;
  console.log(guests1); // 0 if `restaurant.numGuests` is 0, otherwise 10
  ```

- **Using `||`:**
  ```js
  const guests2 = restaurant.numGuests || 10;
  console.log(guests2); // 10 (short circuits on falsy value)
  ```

---

### Nullish Coalescing Operator (`??`)

- **Nullish: `null` and `undefined` (NOT `0` or `''`):**
  ```js
  const guests = restaurant.numGuests ?? 10;
  console.log(guests); // 0 (uses 0 because it's not null/undefined)
  ```

---

### Optional Chaining (`?.`)

- **Checks if a property exists before accessing it:**
  ```js
  console.log(restaurant.openingHours?.mon?.open); // undefined if 'mon' doesn't exist
  ```

---

### Basic Array Operations:

1. **Add Elements:**
   - To the end: `arr.push(element)`
   - To the start: `arr.unshift(element)`

2. **Remove Elements:**
   - From the end: `arr.pop()`
   - From the start: `arr.shift()`

3. **Find Elements:**
   - Index of element: `arr.indexOf(element)`
   - Check if element exists: `arr.includes(element)`

4. **Concatenate Arrays:**
   ```js
   const combined = arr1.concat(arr2);
   // or
   const combined = [...arr1, ...arr2];
   ```

5. **Copy an Array:**
   ```js
   const newArr = [...arr];  // Creates a shallow copy
   ```

---

### Looping Over Arrays:

1. **C++ Style Loop:**
   ```js
   for (let i = 0; i < arr.length; i++) {
     console.log(arr[i]);
   }
   ```

2. **For-of Loop:**
   ```js
   const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];
   for (const item of menu) console.log(item);
   ```

3. **For-of Loop with Index:**
   ```js
   for (const [i, el] of menu.entries()) {
     console.log(`${i + 1}: ${el}`);
   }
   ```

---

### Basic Object Operations:

1. **Add Key-Value Pairs:**
   ```js
   object.newKey = value;
   // or
   object['newKey'] = value;
   ```

2. **Copy an Object:**
   ```js
   const newObject = { ...restaurant };
   ```

3. **Loop Over an Object:**
   ```js
   for (const [key, value] of Object.entries(object)) {
     console.log(`${key}: ${value}`);
   }
   ```

---

### Basic Set Operations:

1. **Create a Set:**
   ```js
   const aSet = new Set(array);
   const bSet = new Set(string);
   ```

2. **Set Operations:**
   - Size of set: `set.size`
   - Check for an element: `set.has(element)`
   - Add an element: `set.add(element)`
   - Delete an element: `set.delete(element)`

---

### Basic Map Operations:

1. **Set Map Values:**
   ```js
   const rest = new Map()
     .set('categories', ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'])
     .set('open', 11)
     .set('close', 23)
     .set(true, 'We are open!')
     .set(false, 'We are closed!');
   ```

2. **Get Map Values:**
   ```js
   console.log(rest.get(true)); // 'We are open!'
   console.log(rest.has('categories')); // true
   ```

---

### Useful Functions:

- **Generate Random Number:**
  ```js
  Math.trunc(Math.random() * 6); // Random number between 0-5
  ```

- **Reverse a String:**
  ```js
  const str = "Hello World";
  const reversed = [...str].reverse().join("");
  console.log(reversed); // "dlroW olleH"
  ```

---

### Scope of Variables:

- `let` and `const` are block-scoped.
- `var` is function-scoped.

---

### Destructuring Arrays:

1. **Basic Destructuring:**
   ```js
   const arr = [2, 3, 4];
   const [x, y, z] = arr;
   console.log(x, y, z); // 2, 3, 4
   ```

2. **Switching Variables:**
   ```js
   let [main, , secondary] = restaurant.categories;
   [main, secondary] = [secondary, main];
   console.log(main, secondary); // Swapped values
   ```

3. **Nested Destructuring:**
   ```js
   const nested = [2, 4, [5, 6]];
   const [i, , [j, k]] = nested;
   console.log(i, j, k); // 2, 5, 6
   ```

---

### Destructuring Objects:

1. **Basic Destructuring:**
   ```js
   const { name: restaurantName, openingHours: hours, categories: tags } = restaurant;
   console.log(restaurantName, hours, tags);
   ```

2. **Mutating Variables:**
   ```js
   let a = 111;
   let b = 999;
   const obj = { a: 23, b: 7, c: 14 };
   ({ a, b } = obj); // Remember to wrap in parentheses
   console.log(a, b); // 23, 7
   ```

3. **Nested Object Destructuring:**
   ```js
   const { fri: { open: o, close: c } } = restaurant.openingHours;
   console.log(o, c); // Friday's opening and closing time
   ```

---

These are the essential JavaScript concepts involving arrays, objects, sets, maps, and common operations like destructuring, spread/rest operators, and more.

### String Methods in JavaScript

---

1. **Get the length of a string:**
   ```js
   str.length;
   ```

2. **Get the starting index of a character or substring:**
   ```js
   str.indexOf('r');
   ```

3. **Get the last index of a character or substring:**
   ```js
   str.lastIndexOf('r');
   ```

4. **Slice the string between starting and ending indices:**
   ```js
   console.log(airline.slice(4, 7)); // Extracts characters from index 4 to 7
   ```
   - If the last index is not specified, it slices to the end of the string.
   - You can also slice from the end with negative indices:
     ```js
     str.slice(1, -1); // Removes the first and last character
     ```

5. **Fix capitalization in a name:**
   ```js
   const passenger = 'jOnAS';
   const passengerLower = passenger.toLowerCase();
   const passengerCorrect = passengerLower[0].toUpperCase() + passengerLower.slice(1);
   console.log(passengerCorrect); // Jonas
   ```

6. **Remove whitespaces from the beginning and end of a string:**
   ```js
   str.trim();
   ```

7. **Replace part of a string:**
   ```js
   str.replace('$', '@');      // Replaces the first occurrence of '$' with '@'
   str.replaceAll('$', '@');   // Replaces all occurrences of '$' with '@'
   ```

8. **Check if a string includes a character or substring:**
   ```js
   str.includes('air');
   ```

9. **Check if a string starts or ends with a specific substring:**
   ```js
   str.startsWith('Air');
   str.endsWith('plane');
   ```

10. **Split a string based on a delimiter (creates an array):**
    ```js
    const words = str.split(' ');
    console.log(words); // Splits the string into an array of words
    ```

11. **Join an array to form a string with a delimiter:**
    ```js
    const sentence = arr.join(' ');
    console.log(sentence); // Joins the array elements into a string
    ```

12. **String Padding:**
    - **`padStart(targetLength, padString)`**: Adds padding at the beginning of the string.
      ```js
      str.padStart(10, '0'); // Pads the string to a length of 10 with '0's
      ```

    - **`padEnd(targetLength, padString)`**: Adds padding at the end of the string.
      ```js
      str.padEnd(10, '.'); // Pads the string to a length of 10 with dots (.)
      ```

13. **Repeat a string multiple times:**
    ```js
    str.repeat(5); // Repeats the string 5 times
    ```

---

### Practical Example: Formatting Flight Information

Given the following string of flight details:
```js
const flights =
  '_Delayed_Departure;fao93766109;txl2133758440;11:25+_Arrival;bru0943384722;fao93766109;11:45+_Delayed_Arrival;hel7439299980;fao93766109;12:05+_Departure;fao93766109;lis2323639855;12:30';
```

We want to format it into human-readable flight information:

```js
const getCode = str => str.slice(0, 3).toUpperCase();

for (const flight of flights.split('+')) {
  const [type, from, to, time] = flight.split(';');
  const output = `${type.startsWith('_Delayed') ? '🔴' : ''}${type.replaceAll(
    '_',
    ' '
  )} ${getCode(from)} ${getCode(to)} (${time.replace(':', 'h')})`.padStart(36);
  console.log(output);
}
```

The output will look like:

```
🔴 Delayed Departure from FAO to TXL (11h25)
         Arrival from BRU to FAO (11h45)
🔴 Delayed Arrival from HEL to FAO (12h05)
         Departure from FAO to LIS (12h30)
```

In this example:
- We extract and format the relevant information (type of flight, departure/arrival airports, and time).
- We conditionally add a warning icon (🔴) for delayed flights.
- We pad the final output for a cleaner display using `padStart()`.

---

These string methods provide powerful tools for handling and manipulating strings in JavaScript.
