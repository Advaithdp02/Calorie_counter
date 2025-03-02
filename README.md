# Calorie Counter Documentation

## Overview
The **Calorie Counter** is a JavaScript-based web application that helps users track their daily calorie intake and expenditure. Users can add meal and exercise entries, set a calorie budget, and calculate their remaining calories. The app ensures input validation and provides real-time feedback on surplus or deficit calorie consumption.

---

## Features
- **Add meal entries** (Breakfast, Lunch, Dinner, Snacks) with calorie values.
- **Add exercise entries** to track burned calories.
- **Set a calorie budget** to maintain daily intake goals.
- **Automatic calculation** of remaining calories.
- **Input validation** to prevent invalid or exponential values.
- **Clear functionality** to reset all entries.

---

## HTML Elements & Structure
### Input Elements:
- **Calorie Budget Input** (`#budget`) - Sets the total calorie budget.
- **Dropdown Selector** (`#entry-dropdown`) - Allows selecting a meal or exercise entry category.
- **Add Entry Button** (`#add-entry`) - Adds input fields for a new entry.
- **Clear Button** (`#clear`) - Resets all input fields.
- **Form Submission** (`#calorie-counter`) - Triggers calorie calculation.
- **Output Section** (`#output`) - Displays calorie calculations.

---

## Functions and Implementation

### 1. `cleanInputString(str)`
- Removes `+`, `-`, and spaces from the input string to ensure numeric input.
- **Regex Used:** `/[+-\s]/g`

### 2. `isInvalidInput(str)`
- Checks for exponential notation (e.g., `1e5`), which is considered invalid.
- **Regex Used:** `/\d+e\d+/i`

### 3. `addEntry()`
- Dynamically adds new input fields for meal/exercise entries under the selected category.
- Labels inputs as `Entry X Name` and `Entry X Calories` where `X` is the entry number.
- **Input Types:** `text` for name, `number` for calorie count.

### 4. `calculateCalories(event)`
- **Prevents form submission default behavior.**
- Retrieves all calorie input values for each category.
- Calls `getCaloriesFromInputs()` to validate and sum calories.
- Computes:
  - **Consumed Calories:** Sum of all meal calories.
  - **Remaining Calories:** `Budget - Consumed + Exercise`
  - **Deficit or Surplus:** Indicates if user exceeded or stayed within the budget.
- Updates the `#output` section with calculated values.

### 5. `getCaloriesFromInputs(list)`
- Iterates through input elements and processes calorie values.
- Calls `cleanInputString()` to sanitize input.
- Calls `isInvalidInput()` to check for invalid exponential notation.
- Returns `null` if invalid input is detected, otherwise sums up values.

### 6. `clearForm()`
- Resets all input fields and clears dynamically added entries.
- Hides the output display.

---

## Event Listeners
```javascript
addEntryButton.addEventListener("click", addEntry);
calorieCounter.addEventListener("submit", calculateCalories);
```
- **`addEntry` event:** Triggers new entry field creation.
- **`submit` event:** Calculates and displays calorie summary.

---

## Usage Instructions
1. **Enter a calorie budget** in the budget input field.
2. **Select a category** (Breakfast, Lunch, Dinner, Snacks, or Exercise) from the dropdown.
3. **Click 'Add Entry'** to add fields for food or exercise details.
4. **Input names and calorie values** for each entry.
5. **Click 'Calculate'** to see results.
6. **Check the output section** for total consumed, burned, and remaining calories.
7. **Click 'Clear'** to reset all fields.

---

## Error Handling & Validation
- **Invalid exponential inputs (e.g., `1e5`) trigger an alert** and prevent calculation.
- **Negative calorie values are not allowed.**
- **Empty input fields are ignored.**

---

## Future Enhancements
- **Persistent data storage** using LocalStorage.
- **Graphical calorie breakdown** using charts.
- **User authentication and profile tracking.**

---

This documentation ensures a clear understanding of the **Calorie Counter** application, its features, and its functionality. 🚀

