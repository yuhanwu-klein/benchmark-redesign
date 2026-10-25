# Penny PRD v1.2

Penny is a personal budgeting app for people in their 20s who get paid monthly and want to stop running out of money before payday. iOS first; Android in 2027.

## 1. Product

**The one job:** help people notice early when their spending is heading somewhere they will regret, while there is still time to change it.

**Users:** 12 interviews (Aug 2026). 9 of 12 said they "set a budget once and never looked at it again". 7 of 12 only noticed overspending after their card was declined or rent was due. 5 of 12 felt "judged" by red warning screens in other apps.

## 2. Design rules

- One accent color (teal). Red is reserved for errors, never for spending.
- No streaks, badges or confetti.
- Every number on screen must say what period it covers.
- Notifications: at most one per day.

## 3. Transactions

Transactions sync from the bank. Each has a merchant, amount, date and a category chosen automatically; the user can change the category.

## 4. Budgets

- The user creates a monthly budget per category (Food, Transport, Shopping, Fun, Bills).
- The Budgets tab lists each category with a progress bar: spent / limit.
- When spending passes the limit, the bar turns red and the app sends a push notification: "You went over your Food budget."
- Budgets reset on the 1st of each month.
- There is no way to move money between categories.

## 5. Insights

A monthly report on the 1st: total spent per category, compared with last month.

## 6. Decision log

| Problem | Decision | Why | Source |
| --- | --- | --- | --- |
| Manual entry was abandoned | Bank sync only | 10 of 12 stopped manual tracking within two weeks | Interviews |
