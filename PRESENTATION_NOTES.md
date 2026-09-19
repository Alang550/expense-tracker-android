# Presentation Notes - Expense Tracker

## The Pitch
Expense Tracker is a modern Android application built to simplify personal finance management. It leverages Jetpack Compose for a responsive UI and Room for reliable local data storage. With features like time-aware greetings, localized currency support, and interactive spending charts, it provides a tailored experience for users to monitor their financial health effectively.

## Original vs Changed
- **Package Name:** Migrated from `com.codewithfk.expensetracker.android` to `com.alangdorcas.expensetracker.android` across all files and directory structures.
- **Identity:** Updated app name to "Expense Tracker" and personalized the home screen with "Alang" and a time-aware greeting (Morning/Afternoon/Evening).
- **Theme:** Standardized the app's accent color to `#2F7E79` (Zinc) and disabled dynamic coloring for consistent branding across Android versions.
- **Localization:** Configured currency formatting to `en-KE` (Kenyan Shilling) and updated input fields to display `KSh` symbols.
- **Categories:** Refined income and expense categories to include items like Tuition, Savings, and Allowance.
- **Icons:** Simplified the transaction list by using generic income/expense icons instead of brand-specific ones.
- **Architecture:** Restructured files into feature-based packages for better maintainability.

## Architecture Map
- **Presentation:** Jetpack Compose screens in `feature/` packages, using ViewModels to manage state.
- **Dependency Injection:** Hilt provides database and DAO instances via `di/DatabaseModule.kt`.
- **Data Layer:** Room database defined in `data/ExpenseDatabase.kt` with entities in `data/model/` and DAOs in `data/dao/`.
- **Navigation:** `NavHostScreen.kt` defines the application's navigation graph and bottom bar.

## 3-Minute Demo Script
1. **Introduction:** Open the app to the Home Screen. Highlight the "Good [Time]" greeting and the name "Alang".
2. **Current Balance:** Show the dashboard showing balance, income, and expenses in `KSh`.
3. **Adding Income:** Tap the FAB, select "Income". Enter "Salary" and "50000". Note the `KSh` prefix. Save.
4. **Adding Expense:** Tap the FAB, select "Expense". Choose "Rent" and enter "15000". Save.
5. **Transaction List:** Tap "See All" to show the history. Observe the unified income/expense icons.
6. **Analytics:** Navigate to the Stats tab to view the line chart visualization.

## Audience Q&A
1. **How is the data persisted?** It uses Room Database. See [ExpenseDatabase.kt](file:///Users/alangdorcas/Downloads/expense-tracker-android/app/src/main/java/com/alangdorcas/expensetracker/android/data/ExpenseDatabase.kt).
2. **How does the app handle different screen sizes?** The UI is built with Jetpack Compose, which is adaptive by nature. [HomeScreen.kt](file:///Users/alangdorcas/Downloads/expense-tracker-android/app/src/main/java/com/alangdorcas/expensetracker/android/feature/home/HomeScreen.kt) uses `ConstraintLayout`.
3. **How did you implement the currency localization?** The `formatCurrency` utility in [Utils.kt](file:///Users/alangdorcas/Downloads/expense-tracker-android/app/src/main/java/com/alangdorcas/expensetracker/android/utils/Utils.kt) was updated to use the `en-KE` locale.
4. **Where is the navigation logic?** centralized in [NavHostScreen.kt](file:///Users/alangdorcas/Downloads/expense-tracker-android/app/src/main/java/com/alangdorcas/expensetracker/android/NavHostScreen.kt).
5. **How does the greeting change based on time?** It uses `java.util.Calendar` to check the current hour.
6. **What library is used for the charts?** MPAndroidChart.
7. **How are dependencies managed?** Dagger Hilt. See [DatabaseModule.kt](file:///Users/alangdorcas/Downloads/expense-tracker-android/app/src/main/java/com/alangdorcas/expensetracker/android/di/DatabaseModule.kt).
8. **Can users add custom categories?** Currently they are static lists in [AddExpense.kt](file:///Users/alangdorcas/Downloads/expense-tracker-android/app/src/main/java/com/alangdorcas/expensetracker/android/feature/add_expense/AddExpense.kt), but the architecture supports future DB-driven categories.

---

**Credits**
Based on the Expense Tracker tutorial project by CodeWithFK (github.com/furqanullah717/expense-tracker-android).
