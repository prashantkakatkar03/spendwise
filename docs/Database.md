# SpendWise Database Design

## User

Stores user information.

Fields:

- user_id
- name
- city
- monthly_income
- created_date


## Transactions

Stores all bank transactions.

Fields:

- transaction_id
- user_id
- transaction_date
- description
- amount
- transaction_type
- category
- merchant
- confidence_score


## Categories

Expense categories.

Examples:

- Food
- Travel
- Shopping
- Bills
- Entertainment
- Healthcare
- Transfer
- Investment


## Merchant Knowledge

Stores merchant intelligence.

Example:

Merchant:
BMTC

Category:
Travel

Alternative:
Monthly Pass

Recommendation:
Compare monthly pass savings


## User Learning

Stores corrections from users.

Example:

Transaction:
ABC Hardware

User classified:
House Construction

Next time:
Automatically classify as House Construction
