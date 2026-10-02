# Test Plan - PrintXpress Android App

This document outlines the testing strategy, test data, and test cases designed to verify the functionality of the **PrintXpress** digital printing service mobile application.

---

## 1. Registration Module Test Cases

| Test Case ID | Test Scenario | Input Data | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|
| **REG-01** | Register with empty fields | Name: `""`<br>Email: `""`<br>Phone: `""`<br>Password: `""` | Show Toast: `"Please fill in all fields"` | As expected | Pass |
| **REG-02** | Register with invalid email format | Name: `"Janith Perera"`<br>Email: `"janith.gmail.com"` (no @)<br>Phone: `"0771234567"`<br>Password: `"123456"` | Show error on Email field: `"Enter a valid email address"` | As expected | Pass |
| **REG-03** | Register with phone number less than 10 digits | Name: `"Janith Perera"`<br>Email: `"janith@gmail.com"`<br>Phone: `"077123"` (6 digits)<br>Password: `"123456"` | Show error on Phone field: `"Phone number must be at least 10 digits"` | As expected | Pass |
| **REG-04** | Register with password less than 6 characters | Name: `"Janith Perera"`<br>Email: `"janith@gmail.com"`<br>Phone: `"0771234567"`<br>Password: `"1234"` (4 chars) | Show error on Password field: `"Password must be at least 6 characters"` | As expected | Pass |
| **REG-05** | Successful registration | Name: `"Janith Perera"`<br>Email: `"janith@gmail.com"`<br>Phone: `"0771234567"`<br>Password: `"password123"` | - Save to Firestore collection `users`<br>- Show Toast: `"Registration Successful"`<br>- Redirect to `LoginActivity` | As expected | Pass |

---

## 2. Login Module Test Cases

| Test Case ID | Test Scenario | Input Data | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|
| **LGN-01** | Login with empty fields | Email: `""`<br>Password: `""` | Show Toast: `"Please fill in all fields"` | As expected | Pass |
| **LGN-02** | Login with unregistered email | Email: `"unknown@gmail.com"`<br>Password: `"password123"` | Show Toast: `"Invalid Email or Password"` | As expected | Pass |
| **LGN-03** | Login with wrong password | Email: `"janith@gmail.com"`<br>Password: `"wrongpass"` | Show Toast: `"Invalid Email or Password"` | As expected | Pass |
| **LGN-04** | Successful login | Email: `"janith@gmail.com"`<br>Password: `"password123"` | - Cache credentials in `SharedPreferences`<br>- Show Toast: `"Login Successful"`<br>- Open `MainActivity` dashboard | As expected | Pass |

---

## 3. Order Customization & Submission Test Cases

| Test Case ID | Test Scenario | Input Data | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|
| **ORD-01** | Submit order with non-numeric quantity | Quantity: `"abc"`<br>Paper Type: `"Art Paper (Glossy)"`<br>Size: `"A4 Standard"`<br>Custom Text: `"Logo print"` | - Log.e() error captured<br>- Show field error: `"Quantity must be a valid number"` | As expected | Pass |
| **ORD-02** | Submit order with zero or negative quantity | Quantity: `0` or `-5`<br>Paper Type: `"Art Paper (Glossy)"`<br>Size: `"A4 Standard"`<br>Custom Text: `"Logo print"` | Show field error: `"Quantity must be greater than zero"` | As expected | Pass |
| **ORD-03** | Submit order without selecting Paper Type | Quantity: `10`<br>Paper Type: `-- Select Paper Type --`<br>Size: `"A4 Standard"`<br>Custom Text: `"Logo print"` | Show Toast: `"Please select a Paper Type"` | As expected | Pass |
| **ORD-04** | Submit order without selecting Size | Quantity: `10`<br>Paper Type: `"Art Paper (Glossy)"`<br>Size: `-- Select Size --`<br>Custom Text: `"Logo print"` | Show Toast: `"Please select a Document Size"` | As expected | Pass |
| **ORD-05** | Submit order with empty custom text | Quantity: `10`<br>Paper Type: `"Art Paper (Glossy)"`<br>Size: `"A4 Standard"`<br>Custom Text: `""` | Show field error: `"Custom printing text instruction cannot be empty"` | As expected | Pass |
| **ORD-06** | Successful order submission | Product: `"Visiting Cards"` (LKR 15.00 base)<br>Quantity: `100`<br>Paper Type: `"Art Paper (Glossy)"`<br>Size: `"Business Card"`<br>Custom Text: `"Janith Perera - SE Student"` | - Save to Firestore collection `orders` with `totalPrice = LKR 1500.00` and `status = Pending`<br>- Show Toast: `"Order Submitted Successfully"`<br>- Reset inputs and finish Activity | As expected | Pass |

---

## 4. Order History Test Cases

| Test Case ID | Test Scenario | Database State | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|
| **HST-01** | View history with zero orders | Firestore collection `orders` has no records matching user's `userId` | - Hide list RecyclerView<br>- Display message: `"No Orders Found"` | As expected | Pass |
| **HST-02** | View history with existing orders | Firestore collection `orders` has 2 records matching user's `userId` | - Populates RecyclerView with 2 order cards<br>- Displays: product names, quantities, dates, status badges, and correct prices | As expected | Pass |
