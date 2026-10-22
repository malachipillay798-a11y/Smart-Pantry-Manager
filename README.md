# Smart Pantry Manager

## 1. Project Overview

Smart Pantry Manager is a mobile application developed using **Java in Android Studio**. The purpose of the application is to help users manage ingredients they already have at home and reduce food waste by suggesting recipes that can be prepared using only the available ingredients.

The application allows users to add, view, edit and delete pantry ingredients, check suggested recipes, view recipe instructions, and manage application settings.

A recipe is suggested only when the user has all its required ingredients in sufficient quantities. Recipes that require missing ingredients or more than the available quantity must not appear in the suggested recipes list.

## 2. Project Objectives

The main objectives are to:

- Manage pantry ingredients and their quantities.
- Store ingredient names, units and optional expiry dates.
- Provide full Create, Read, Update and Delete (CRUD) functionality.
- Display a collection of recipes with ingredients and preparation methods.
- Suggest recipes based on the ingredients available in the pantry.
- Prevent recipes from being suggested when ingredients or quantities are insufficient.
- Store application data locally so it remains available after restarting the app.
- Provide a clear, user-friendly Android interface.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Java | Main programming language |
| Android Studio | Android application development environment |
| Android SDK | Android application components and tools |
| SQLite | Local relational database |
| SQLiteOpenHelper | Creating and managing the local database |
| RecyclerView | Displaying recipe information in a list |
| Custom Adapter | Connecting recipe data to the RecyclerView |
| Intents | Navigating between activities and passing data |
| XML resources | Defining the Android manifest and interface resources |

## 4. Main Application Features

### 4.1 Pantry Management

Users can manage ingredients stored in their pantry. Each ingredient can include:

- Ingredient name
- Quantity
- Unit of measurement
- Optional expiry date

Users can add new ingredients, view the pantry list, update existing ingredient details and delete ingredients they no longer have.

The application validates ingredient input to help prevent incomplete or invalid entries.

### 4.2 Recipe Collection

The application includes 20 sample recipes inserted into the database when it is first created. Each recipe contains a name, required ingredients, quantities and preparation instructions.

### 4.3 Suggested Recipes

The suggested recipes feature compares the ingredients required by each recipe against the ingredients stored in the pantry.

The application follows a strict matching rule:

1. Check each required ingredient.
2. Confirm that the ingredient exists in the pantry.
3. Check that the available quantity is sufficient.
4. Exclude the recipe if an ingredient is missing or its quantity is insufficient.
5. Display the recipe only when all required ingredients and quantities are available.

Ingredient matching accounts for basic differences in capitalisation and simple singular/plural forms. The application does not automatically convert between different measurement units, so units must match.

### 4.4 Recipe Details

Users can select a recipe to view its required ingredients, quantities and preparation method.

### 4.5 Settings

The application includes a settings screen where users can manage the available expiry-alert preference.

## 5. Database Design

The application uses a local SQLite database to store its data.

The database contains the following main tables:

- **pantry_items:** Stores pantry ingredients, quantities, units and optional expiry dates.
- **recipes:** Stores recipe names and preparation methods.
- **recipe_ingredients:** Stores the ingredients and quantities required for each recipe.
- **settings:** Stores application preferences.

SQLite allows the application to work without requiring a separate database server or a continuous internet connection. Data is stored locally on the device.

## 6. Application Screens

The application contains the following screens:

1. **Main Screen:** Provides access to the main application features.
2. **Pantry Screen:** Displays and manages pantry ingredients.
3. **Add/Edit Ingredient Screen:** Allows users to enter or update ingredient details.
4. **Recipe Collection Screen:** Displays the available recipes.
5. **Suggested Recipes Screen:** Displays recipes that satisfy the strict ingredient-matching rule.
6. **Recipe Detail Screen:** Displays recipe ingredients and preparation instructions.
7. **Settings Screen:** Provides access to application preferences.

Android Intents are used to navigate between activities and pass relevant information, such as a selected recipe ID.

## 7. Project Structure

The main Java source files include:

- `DatabaseHelper.java` — creates and manages the SQLite database, handles database operations and initial recipe data.
- `PantryItem.java` — represents a pantry ingredient.
- `RecipeIngredient.java` — represents an ingredient required by a recipe.
- `Recipe.java` — represents recipe information.
- `Ui.java` — contains reusable interface-related functionality.
- `RecipeAdapter.java` — displays recipe data using a custom RecyclerView adapter.
- `MainActivity.java` — provides the main navigation screen.
- `PantryActivity.java` — displays and manages pantry items.
- `IngredientFormActivity.java` — handles adding and editing ingredients.
- `RecipeListActivity.java` — displays the recipe collection.
- `SuggestedRecipesActivity.java` — displays recipes matching the pantry contents.
- `RecipeDetailActivity.java` — displays recipe information and preparation instructions.
- `SettingsActivity.java` — manages application settings.

The project also contains Android manifest and resource files, Gradle build files and this README document.

## 8. Requirements

Before opening the project, ensure that you have:

- Android Studio installed.
- A compatible Java Development Kit (JDK 17 is specified for this project setup).
- The Android SDK required by the project's Gradle configuration.
- An Android emulator or a physical Android device for running the application.

## 9. How to Open and Run the Project

1. Extract the Smart Pantry Manager project ZIP file to a folder on your computer.
2. Open Android Studio.
3. Select **Open** from the welcome screen.
4. Navigate to the extracted project folder.
5. Select the folder containing the root `settings.gradle` and `build.gradle` files.
6. Allow Android Studio to synchronise the Gradle project.
7. If prompted, install the required Android SDK components.
8. Create or select an Android emulator, or connect a physical Android device with USB debugging enabled.
9. Wait for Gradle synchronisation to finish and resolve any reported configuration errors.
10. Select the app run configuration and click **Run**.
11. Confirm that the application launches and test its main features.

**Note:** The project should be built and tested in your own Android Studio environment before submission. If Gradle reports a compatibility or SDK error, check the error message and ensure the required JDK and Android SDK versions are installed.

## 10. How to Test the Application

Use the following tests to check the main requirements:

### Test 1: Add an Ingredient
1. Open the pantry screen.
2. Add an ingredient with a name, quantity and unit.
3. Save the ingredient.
4. Confirm that it appears in the pantry list.

### Test 2: Edit and Delete an Ingredient
1. Select an existing pantry ingredient.
2. Change its quantity or other details and save.
3. Confirm that the updated information appears.
4. Delete the ingredient and confirm that it no longer appears.

### Test 3: Strict Recipe Matching
1. Add all the ingredients required for a recipe in sufficient quantities.
2. Open Suggested Recipes.
3. Confirm that the recipe appears.
4. Reduce a required quantity below the recipe's requirement or remove a required ingredient.
5. Refresh or reopen the suggestions screen.
6. Confirm that the recipe is excluded.

### Test 4: Recipe Details
1. Open a suggested recipe.
2. Confirm that its required ingredients, quantities and preparation instructions are displayed.

### Test 5: Data Persistence
1. Add an ingredient.
2. Close and reopen the application.
3. Confirm that the ingredient remains stored.

### Test 6: Empty Suggestions
1. Ensure the pantry does not contain all ingredients for any recipe.
2. Open Suggested Recipes.
3. Confirm that no incomplete recipe is suggested and that the empty state is displayed.

## 11. Limitations

- Ingredient quantities must use compatible units because automatic unit conversion is not implemented.
- Ingredient name normalisation supports only basic case and singular/plural differences.
- The database is stored locally on the device; synchronisation between devices is not provided.
- Recipe suggestions depend on the accuracy of the ingredients and quantities entered by the user.
- The application should be tested on an emulator or physical device to confirm that all features work correctly.

## 12. Future Improvements

Possible future enhancements include:

- Automatic conversion between compatible measurement units.
- More advanced ingredient-name matching.
- Notifications for ingredients approaching their expiry dates.
- The ability to create and save custom recipes.
- Exporting pantry data and backing it up.
- Cloud synchronisation across multiple devices.



