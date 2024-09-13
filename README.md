# React Native with SQLite

## Overview

This app fetches menu items from a remote API, saves them into a SQLite database, and displays them in a `SectionList`. Users can search and filter menu items by categories such as "Appetizers," "Salads," and "Beverages." The app utilizes React Native, SQLite for local storage, and React hooks for state management.

## Setup and Installation

1.  **Clone the repository**:  
    Clone the project repository to your local machine.
2.  **Install dependencies**:  
    Run the following command to install the required dependencies:

    bash

    Copy code

    `npm install`

3.  **Running the application**:  
    To run the app on an emulator or device, use:

    bash

    Copy code

    `npm expo start`

    Follow the prompts to run on iOS, Android, or in a web browser.

## Key Components and Functions

### 1. **`App.js`**

This file is the main entry point of the app. It handles fetching data, managing state, and rendering UI components.

- **State Variables:**

  - `data`: Stores the sectioned list data.
  - `searchBarText`: Text entered in the search bar.
  - `query`: Search query used to filter menu items.
  - `filterSelections`: Array to keep track of which category filters are selected.

- **Key Functions:**

  - `fetchData()`: Fetches menu items from the API and transforms the data to flatten category titles.
  - `useEffect()`: Initializes the SQLite database, fetches data if the database is empty, and loads data into the app state.
  - `useUpdateEffect()`: Custom hook used to update data when search query or filters change.
  - `handleSearchChange()`: Updates search bar text and debounces the lookup query.
  - `handleFiltersChange()`: Toggles filter selections for categories.

- **Components Rendered:**

  - `Searchbar`: A search bar component from `react-native-paper` for inputting search queries.
  - `Filters`: Custom component for category filters.
  - `SectionList`: Displays the menu items grouped by categories.

### 2. **`database.js`**

Handles SQLite database operations for storing and retrieving menu items.

- **Functions:**
  - `createTable()`: Creates the `menuitems` table if it doesn't exist.
  - `getMenuItems()`: Retrieves all menu items from the database.
  - `saveMenuItems(menuItems)`: Saves menu items to the database using SQL transactions.
  - `filterByQueryAndCategories(query, activeCategories)`: Filters menu items by search query and selected categories using SQL.

### 3. **`utils.js`**

Contains utility functions and hooks.

- **Functions:**
  - `getSectionListData(data)`: Transforms flat data into sectioned data structure required by `SectionList`.
  - `useUpdateEffect(effect, dependencies)`: Custom hook that runs an effect only on updates, not on initial mount.

### 4. **`Filters.js`**

A custom component (not fully shown in the initial code) for handling filter selections based on categories.

## Data Flow

1.  **Fetching Data:**

    - The app fetches data from a remote API URL (`API_URL`) using `fetchData()` function.
    - The fetched data is transformed to flatten the category object into a string field (`category`).

2.  **Storing Data:**

    - Data is saved into a SQLite database using `saveMenuItems()`.

3.  **Retrieving Data:**

    - On app start, data is loaded from the database using `getMenuItems()`.

4.  **Filtering and Display:**

    - Data is filtered by search query and selected categories using `filterByQueryAndCategories()`.
    - The filtered data is formatted using `getSectionListData()` and displayed in a `SectionList`.

## Error Handling

- Errors during data fetching or database operations are caught and displayed using `Alert.alert()` to notify the user.

## Dependencies

- **React Native**: Core framework for building the app.
- **Expo**: Development platform for running React Native apps.
- **SQLite**: Database used for storing menu items locally.
- **React Native Paper**: UI components library for the search bar.
- **Lodash.debounce**: Utility for debouncing search input to improve performance.

## Further Improvements

- **Enhance Error Handling**: Add more robust error handling and user notifications.
- **Improve UI**: Customize components further to match specific design requirements.
- **Performance Optimization**: Optimize data fetching and filtering for larger datasets.

## Conclusion

This documentation provides a comprehensive guide to understanding the React Native Menu App. The code structure supports easy extension for additional features such as more categories or advanced filtering options.

---

Let me know if there's anything specific you'd like to add or adjust in the documentation!
