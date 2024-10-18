# recipeappwithflutter🍲

A **Flutter**-based recipe app where users can **add, view, and favorite recipes**. The app uses **Firebase Firestore** to store recipes and user data. Users can create an account, log in, and manage their own recipes. The app also shows **popular and newly added recipes** on the home screen.

## Features ✨
- **User Authentication:**  
  Users can sign up, log in, and manage their profiles using Firebase Authentication.  
- **Add New Recipes:**  
  Users can add recipes with details like category, ingredients, description, and servings.
- **Favorite Recipes:**  
  Users can favorite recipes, and the app tracks the favorite count for each recipe.
- **Popular & New Recipes:**  
  The home screen displays the most popular and newly added recipes.
- **Firestore Integration:**  
  All recipes and user data are stored and fetched from **Firebase Firestore**.

## Technologies Used 🛠️
- **Flutter**: For building the mobile app UI.
- **Firebase Authentication**: For user login and sign-up.
- **Firestore**: For storing recipes and user profiles.
- **Provider**: For state management.

## Screenshots 📱
*Coming soon...* (Feel free to add screenshots here.)

## Installation & Setup 🚀

### Prerequisites
- Flutter SDK installed ([Download Flutter](https://flutter.dev/docs/get-started/install)).
- Firebase project configured ([Firebase Console](https://console.firebase.google.com/)).
- Your own `google-services.json` file for Android and `GoogleService-Info.plist` for iOS.

### Steps to Run the App
1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/recipe-app.git
   cd recipe-app
   ```

2. **Install dependencies**:
   ```bash
   flutter pub get
   ```

3. **Connect Firebase**:
   - Add `google-services.json` in the `android/app` directory.
   - Add `GoogleService-Info.plist` in the `ios/Runner` directory.

4. **Run the app**:
   ```bash
   flutter run
   ```

## Firestore Structure 🗄️

### `Tariflerim` (Recipes Collection)
| Field        | Type       | Example Value                       |
|--------------|------------|-------------------------------------|
| `name`       | String     | "Pancakes"                         |
| `category`   | String     | "Breakfast"                        |
| `createdAt`  | Timestamp  | August 24, 2024 at 11:14:07 UTC    |
| `favoriteCount` | Number  | 15                                  |
| `ingredients` | Array     | ["Flour", "Milk", "Eggs"]          |
| `description` | String    | "Delicious homemade pancakes."     |
| `servings`    | Number    | 2                                   |
| `userId`      | String    | "7lhfQtjrGfeCbdbuPdoClwyLyk72"     |

## Firebase Security Rules 🔒
Example security rules to restrict access to user-specific data:

```javascript
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/favorites/{recipeId} {
      allow read, write: if request.auth.uid == userId;
    }
    match /recipes/{recipeId} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}
```


Enjoy cooking with our recipe app! 🍳
