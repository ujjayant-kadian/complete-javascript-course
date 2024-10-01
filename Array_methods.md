### Array Methods in JavaScript

---

1. **Slice** (Non-mutating method):
   - Extracts a portion of an array without modifying the original array.
   ```js
   console.log(arr.slice(1, -2)); // ['b', 'c']
   console.log(...arr); // Spread the array into individual elements
   ```

2. **Splice** (Mutating method):
   - Modifies the actual array by adding/removing elements.
   ```js
   console.log(arr.splice(-1)); // Removes the last element ('e')
   console.log(arr); // ['a', 'b', 'c', 'd']
   ```

3. **Reverse** (Mutating method):
   - Reverses the array in place.
   ```js
   arr.reverse();
   console.log(arr); // ['d', 'c', 'b', 'a']
   ```

4. **Concat**:
   - Combines two or more arrays.
   ```js
   arr.concat(arr2); // Combines arr with arr2
   ```

5. **Join**:
   - Converts an array to a string with a specified separator.
   ```js
   console.log(arr.join(' - ')); // 'a - b - c - d'
   ```

6. **At Method**:
   - Returns the element at a specified index (supports negative indices).
   ```js
   console.log(arr2.at(-1)); // Returns the last element of arr2 (64)
   ```

---

### Looping Over Arrays

1. **forEach**:
   - Executes a function for each array element.
   ```js
   movements.forEach((mov, i) => {
     if (mov > 0) {
       console.log(`Movement ${i + 1}: You deposited ${mov}`);
     } else {
       console.log(`Movement ${i + 1}: You withdrew ${Math.abs(mov)}`);
     }
   });
   ```

2. **forEach with Maps and Sets**:
   - **Maps**:
     ```js
     currencies.forEach((value, key) => {
       console.log(`${key}: ${value}`);
     });
     ```
   - **Sets**:
     ```js
     currenciesUnique.forEach((value) => {
       console.log(`${value}: ${value}`);
     });
     ```

---

### Array Transformation Methods

1. **Map**:
   - Creates a new array by applying a function to each element.
   ```js
   const movementsUSD = movements.map(mov => mov * eurToUsd);
   ```

2. **Filter**:
   - Filters the array based on a condition.
   ```js
   const withdrawals = movements.filter(mov => mov < 0);
   console.log(withdrawals); // All negative movements
   ```

3. **Reduce**:
   - Reduces the array to a single value (e.g., sum, max).
   ```js
   const balance = movements.reduce((acc, cur) => acc + cur, 0); // Sum of movements
   const max = movements.reduce((acc, mov) => (acc > mov ? acc : mov), movements[0]); // Max value
   ```

4. **Chaining Methods**:
   - You can chain `filter`, `map`, and `reduce` together.
   ```js
   const totalDepositsUSD = movements.filter(mov => mov > 0).map(mov => mov * eurToUsd).reduce((acc, mov) => acc + mov, 0);
   ```

5. **Find**:
   - Finds the first element that satisfies a condition.
   ```js
   const firstWithdrawal = movements.find(mov => mov < 0);
   ```

---

### Checking Conditions

1. **Some and Every**:
   - **Some**: Checks if at least one element meets a condition.
     ```js
     console.log(movements.some(mov => mov > 0)); // true if there's a positive movement
     ```
   - **Every**: Checks if all elements meet a condition.
     ```js
     console.log(movements.every(mov => mov > 0)); // true if all movements are positive
     ```

2. **Separate Callback**:
   - Using separate callback functions for clarity.
   ```js
   const deposit = mov => mov > 0;
   console.log(movements.some(deposit)); // true
   console.log(movements.every(deposit)); // false
   console.log(movements.filter(deposit)); // Filters positive movements
   ```

---

### Flattening Arrays

1. **Flat**:
   - Flattens a nested array.
   ```js
   const arr4 = [[1, 2, 3], [4, 5, 6], 7, 8];
   console.log(arr4.flat()); // [1, 2, 3, 4, 5, 6, 7, 8]
   
   const arrDeep = [[[1, 2], 3], [4, [5, 6]], 7, 8];
   console.log(arrDeep.flat(2)); // Flattens two levels deep
   ```

2. **flatMap**:
   - Combines `map` and `flat` in one method.
   ```js
   const overalBalance = accounts.map(acc => acc.movements).flat().reduce((acc, mov) => acc + mov, 0);
   console.log(overalBalance);

   const overalBalance2 = accounts.flatMap(acc => acc.movements).reduce((acc, mov) => acc + mov, 0);
   console.log(overalBalance2);
   ```

---

### Sorting Arrays

1. **Sort**:
   - Sorts an array in place (default is lexicographical sorting).
   ```js
   const owners = ['Jonas', 'Zach', 'Adam', 'Martha'];
   console.log(owners.sort()); // ['Adam', 'Jonas', 'Martha', 'Zach']

   movements.sort((a, b) => a - b); // Sorts numbers in ascending order
   ```

---

### Creating and Filling Arrays

1. **Creating an Array**:
   - Creates an empty array of specified length.
   ```js
   const x = new Array(7); // [empty x 7]
   ```

2. **Fill**:
   - Fills part of an array with a value.
   ```js
   x.fill(1, 3, 5); // Fills index 3 to 5 with 1: [empty x 3, 1, 1, empty x 2]
   ```

These methods give you powerful tools to work with arrays in JavaScript, whether you're transforming, looping, or manipulating them.