# User Documentation - PrintXpress Mobile App

Welcome to **PrintXpress**, your premium native Android application for digital printing custom orders. This documentation explains how to set up, register, log in, browse products, place custom print requests, and track your history.

---

## 1. Getting Started

When you launch the application for the first time, you will be directed to the **Login Screen**. If you do not have an active account, you must create one first.

### Registering a New Account
1. Click the **Register Here** link at the bottom of the Login Screen.
2. Fill in the registration form:
   - **Full Name**: Enter your complete name (e.g. `Janith Perera`).
   - **Email Address**: Enter a valid email format (e.g. `janith@gmail.com`).
   - **Phone Number**: Enter a valid phone number (must be at least 10 digits, e.g. `0771234567`).
   - **Password**: Choose a secure password (must be at least 6 characters).
3. Click the **REGISTER** button.
4. On success, you will see a `"Registration Successful"` Toast message and be redirected back to the Login Screen.

---

## 2. Signing In

1. On the **Login Screen**, input your registered **Email Address** and **Password**.
2. Click the **LOGIN** button.
3. On successful authentication, you will be redirected to the **Main Dashboard**.
4. *Note: The application saves your session cache. You will not need to sign in again when relaunching the app, unless you explicitly log out.*

---

## 3. Browsing Print Products

1. The **Main Dashboard** displays a list of standard digital printing stock options (e.g. *Visiting Cards, Brochures, Event Posters, Banners, and Custom Stickers*).
2. Each item lists:
   - Product name
   - Material details
   - Standard sizes
   - Base price per copy (in Sri Lankan Rupees - LKR)
3. Select any product from the catalog list to customize your order.

---

## 4. Customizing and Placing an Order

1. Selecting a product from the list opens the **Customize Print Order** screen.
2. Configure your order:
   - **Quantity**: Input the number of print copies you require (must be a number greater than 0).
   - **Paper Type**: Choose a paper stock from the dropdown spinner (e.g., Glossy Art Card, Matte Satin, Photo Paper, Bond).
   - **Size**: Choose your desired print output size from the dropdown spinner (e.g., A4, A3, A5, Business Card size, Poster A2).
   - **Custom Instructions / Print Text**: Enter the custom content or wording you wish to print (e.g. name details for cards, brochure content, banner headlines). This field cannot be empty.
3. Click **SUBMIT ORDER**.
4. The system calculates your total price dynamically (`Base Price * Quantity`).
5. On success, you will see the `"Order Submitted Successfully"` Toast message, and you will be returned to the dashboard.

---

## 5. Tracking Order History

1. In the top right corner of the Main Dashboard Toolbar, click the **My Orders** option (page list icon).
2. The **Order History** page lists all print orders placed under your account.
3. Each order card displays:
   - Product Name
   - Quantity ordered
   - Total calculated price (LKR)
   - Dynamic status badge:
     - **Pending**: Order successfully recorded and awaiting queue processing.
     - **Printing**: Currently on the digital press.
     - **Ready**: Finished cutting and packaging, ready for pickup.
     - **Cancelled**: Terminated order.
   - Order Date & Time.
4. If you have not placed any orders yet, you will see the message `"No Orders Found"`.
5. Press the top-left back arrow to return to the Dashboard.

---

## 6. Logging Out

1. To sign out, click the **three vertical dots** (options menu button) in the top-right corner of the Main Dashboard Toolbar.
2. Select **Logout**.
3. This clears your local cache session and returns you to the **Login Screen**.
