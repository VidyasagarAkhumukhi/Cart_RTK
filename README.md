# React Shopping Cart with Redux Toolkit

[![React](https://img.shields.io/badge/React-^18-blue?logo=react)](https://react.dev/)
[![Redux Toolkit](https://img.shields.io/badge/Redux%20Toolkit-^1.9-764ABC?logo=redux)](https://redux-toolkit.js.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📝 Description

This project is a fully functional shopping cart application built with React, demonstrating modern and efficient state management using **Redux Toolkit**. The application fetches product data asynchronously from a remote API, displays the items in a cart, and allows users to perform standard cart operations. It showcases the use of slices for feature-based state management, `createAsyncThunk` for handling asynchronous API calls, and a modal for user confirmations, providing a comprehensive example of a real-world Redux implementation.

## ✨ Features

* **Asynchronous Data Fetching:** Initializes the cart by fetching product data from an API using Redux Toolkit's `createAsyncThunk`.
* **Stateful Cart Management:**
    * Increase or decrease the quantity of individual items.
    * Remove a specific item from the cart.
    * Clear all items from the cart with a confirmation modal.
* **Dynamic Calculations:** Automatically calculates and displays the total number of items and the total cost of the cart.
* **Centralized State:** Manages all application state (cart items, loading status, modal visibility) within the Redux store.
* **Loading State:** Displays a loading indicator while initial data is being fetched.
* **Confirmation Modal:** A reusable modal component, managed by its own Redux slice, prompts the user for confirmation before clearing the cart.

## 🚀 Live Demo

<!-- Optional: Add a link to your deployed application -->
[Link to Live Demo](#) <!-- Replace '#' with your deployment URL -->

## 🛠️ Technologies Used

* **Frontend:** React.js
* **State Management:**
    * `@reduxjs/toolkit`
    * `react-redux`
* **HTTP Client:** `axios` (for API requests within the async thunk)
* **API:** `course-api.com` for fetching product data.
* **Styling:** CSS

## ⚙️ Setup and Installation

To run this project locally, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/VidyasagarAkhumukhi/Cart_RTK
    cd <your-repository-directory-name>
    ```

2.  **Install dependencies:**
    Make sure you have Node.js and npm (or yarn) installed.
    ```bash
    npm install
    # or
    yarn install
    ```

3.  **Run the development server:**
    ```bash
    npm run start
    # or
    npm run dev
    ```
    This will typically open the application in your default browser at `http://localhost:3000` (for Create React App) or `http://localhost:5173` (for Vite).

## 💡 Redux Toolkit Implementation

This project effectively utilizes Redux Toolkit to manage application state, adhering to modern Redux best practices.

* **`configureStore`**: Sets up the Redux store (`store.js`) with the `cart` and `modal` reducers, and automatically includes the Redux DevTools Extension for easy debugging.

* **`createSlice`**: State logic is organized into feature-based "slices":
    * **`cartSlice.js`**: Manages all state related to the shopping cart, including `cartItems`, `amount`, `total`, and `isLoading`. It contains reducers for synchronous actions like `clearCart`, `removeItem`, `increase`, and `decrease`.
    * **`modalSlice.js`**: A separate slice to manage the UI state of the confirmation modal (`isOpen`), demonstrating how to handle non-domain state in Redux.

* **`createAsyncThunk`**: The `getCartItems` function in `cartSlice.js` handles the asynchronous logic of fetching initial product data from the API. It automatically dispatches lifecycle actions (`pending`, `fulfilled`, `rejected`) which are handled by `extraReducers`.

* **`extraReducers`**: This section in `cartSlice.js` responds to the actions dispatched by `createAsyncThunk`. It sets `isLoading` to `true` when the request is pending, populates `cartItems` when it's fulfilled, and handles the `isLoading` state on rejection.

* **React-Redux Hooks**:
    * **`useSelector`**: Used in components (`Navbar`, `CartContainer`, `App`) to read data from the Redux store without prop drilling.
    * **`useDispatch`**: Used in components (`CartItem`, `CartContainer`, `Modal`) to dispatch actions (e.g., `removeItem({ id })`, `openModal()`) to the store.

## 🏗️ Project Structure

* `src/`: Main source code directory.
    * `components/`: Reusable React components.
        * `CartContainer.js`: Displays the list of cart items or an "empty cart" message.
        * `CartItem.js`: Renders a single item with controls for quantity and removal.
        * `Modal.js`: The confirmation dialog for clearing the cart.
        * `Navbar.js`: Displays the application title and total item count.
    * `features/`: Contains Redux Toolkit logic separated by feature.
        * `cart/cartSlice.js`: Slice for cart-related state and actions.
        * `modal/modalSlice.js`: Slice for modal-related state and actions.
    * `App.js`: Main application component, fetches initial data and manages modal visibility.
    * `store.js`: Configures and exports the Redux store.
    * `cartItems.js`: (Likely for initial static data or fallback).
    * `icons.js`: SVG icons used in the application.
    * `index.js`: Application entry point, wraps `App` in the Redux `<Provider>`.
    * `index.css`: Global CSS styles.
* `public/`: Static assets.
* `package.json`: Project dependencies and scripts.

## 🤝 Contributing

Contributions are welcome! Please follow standard fork, branch, and pull request workflows.

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-awesome-feature`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'Add some awesome feature'`).
5.  Push to the branch (`git push origin feature/your-awesome-feature`).
6.  Open a Pull Request.

## 📄 License

This project is licensed under the MIT License.

---

_This README provides a comprehensive guide to the React & Redux Toolkit Shopping Cart application._
