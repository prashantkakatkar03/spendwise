# SpendWise Recommendation Engine

## Purpose

The Recommendation Engine analyzes user transactions and identifies opportunities where users can save money or get better value without reducing their lifestyle.

---

# Rule 1: Travel Optimization

## Problem

Users often pay for travel individually without knowing whether a pass or card would provide better value.

## Detect

SpendWise should check:

- Is the transaction related to travel?
- Is the same travel merchant appearing repeatedly?
- Is monthly travel spending increasing?

Examples:

- BMTC
- Namma Metro
- Uber
- Ola
- Rapido

## Decision

IF:

- Travel transactions are frequent
- Monthly spending crosses a defined limit

THEN:

Suggest:

- Monthly pass
- Travel card
- Better payment option

## Example

User spends:

₹1500/month on BMTC tickets
---

# Rule 2: Food Optimization

## Problem

Users often spend extra money on food delivery charges, platform fees, and convenience charges without realizing the additional cost.

## Detect

SpendWise should check:

- Is the transaction related to food?
- Is the user frequently ordering food?
- Is monthly food delivery spending increasing?

Examples:

- Swiggy
- Zomato
- Restaurants
- Cafes

## Decision

IF:

- Food delivery transactions are frequent
- Monthly spending crosses a defined limit

THEN:

Suggest:

- Direct restaurant ordering
- Pickup option
- Subscription comparison
- Better value alternatives

## Example

User spends:

₹3000/month on food delivery

SpendWise recommendation:

"Your food delivery spending is ₹3000 this month. Ordering directly from restaurants or choosing pickup options may reduce additional charges."
---

# Rule 3: Recharge Optimization

## Problem

Users often recharge their mobile plans every month without comparing whether a long-term plan provides better value.

## Detect

SpendWise should check:

- Is the transaction related to mobile recharge?
- Is the same telecom provider appearing repeatedly?
- Is the recharge happening at regular intervals?

Examples:

- Jio
- Airtel
- Vi
- BSNL

## Decision

IF:

- User performs regular monthly recharges
- A suitable annual or longer-term plan may reduce cost

THEN:

Suggest:

- Compare monthly and annual plans
- Check available better-value plans

## Example

User spends:

₹299 every month on recharge

Yearly cost:

₹3588

SpendWise recommendation:

"You recharge every month with the same plan. Compare annual plans to check if you can reduce your yearly mobile expense."

SpendWise recommendation:

"Based on your travel frequency, a monthly pass or travel card may provide better value. Check possible savings before your next recharge."
---

# Rule 4: Shopping Optimization

## Problem

Users may spend more on online shopping because they do not compare prices or notice repeated purchases.

## Detect

SpendWise should check:

- Is the transaction related to shopping?
- Is the user purchasing frequently?
- Is the same category being purchased repeatedly?

Examples:

- Amazon
- Flipkart
- Meesho
- Myntra

## Decision

IF:

- Shopping transactions are frequent
- Similar purchases appear repeatedly

THEN:

Suggest:

- Compare prices across platforms
- Check alternative products
- Review before purchasing non-essential items

## Example

User spends:

₹5000/month on online shopping

SpendWise recommendation:

"You frequently purchase online. Compare prices before buying and review repeated purchases to identify possible savings."
# Rule 5: Self Transfer Detection 🔄

## Problem

Users may transfer money between their own accounts, wallets, or credit cards. If SpendWise treats these transactions as income or expenses, it can create incorrect financial insights.

## Detect

SpendWise should check:

- Is the transaction a transfer between user's own accounts?
- Are both sender and receiver accounts owned by the same user?
- Does the transaction description indicate a transfer?

Examples:

- HDFC Savings → SBI Savings
- Salary Account → Personal Savings Account
- Bank Account → Own Wallet
- Bank Account → Credit Card Payment

## Decision

IF:

- Money is moved between user's own accounts
- Sender and receiver belong to the same user

THEN:

Classify as:

- Self Transfer
- Do not count as income
- Do not count as expense
- Track only for account balance movement

## Example

User transfers:

₹10,000 from HDFC Savings Account to SBI Savings Account

SpendWise recommendation:

"Self-transfer detected. This transaction will not be included in your income or expense calculations."
# Rule 6: Salary / Income Detection 💰

## Problem

Users receive different types of income such as salary, freelance payments, business income, or other credits. SpendWise needs to identify genuine income transactions and avoid marking transfers or refunds as income.

## Detect

SpendWise should check:

- Is the transaction a credit into the user's account?
- Does the transaction description indicate salary or income?
- Is the source of money from an employer, client, or income source?

Examples:

- Salary Credit
- Monthly Payroll
- Freelance Payment
- Business Income
- Interest Income
- Rental Income

## Decision

IF:

- Money is credited into the user's account
- Transaction matches known income patterns

THEN:

Classify as:

- Income
- Identify income source
- Include in income calculation
- Exclude from expense analysis

## Example

User receives:

₹70,000 credited with description "SALARY HRS NAVIGATION"

SpendWise recommendation:

"Salary income detected. Your monthly income of ₹70,000 has been added to your financial overview."
# Rule 7: Subscription Detection 🔁

## Problem

Users often subscribe to multiple services but may forget about recurring payments. These unnoticed subscriptions can increase monthly expenses and reduce savings.

## Detect

SpendWise should check:

- Is the transaction repeated at regular intervals?
- Is the payment made to a subscription-based service?
- Does the same merchant charge a similar amount every month?

Examples:

- Netflix
- Amazon Prime
- Spotify
- YouTube Premium
- Software subscriptions
- OTT platforms
- Gym memberships

## Decision

IF:

- Same merchant transaction occurs repeatedly
- Payment frequency is monthly, yearly, or recurring

THEN:

Suggest:

- Review active subscriptions
- Cancel unused subscriptions
- Check if cheaper alternatives are available

## Example

User pays:

₹649/month for an OTT subscription

SpendWise recommendation:

"You have a recurring subscription of ₹649/month. Review your subscriptions and cancel services you no longer use to save money."
# Rule 8: Duplicate Transaction Detection ⚠️

## Problem

Users may accidentally make duplicate payments due to payment failures, repeated clicks, or merchant errors. SpendWise should identify possible duplicate transactions to prevent unnecessary expenses.

## Detect

SpendWise should check:

- Are there multiple transactions with the same merchant?
- Are the transaction amounts identical or very similar?
- Did the transactions occur within a short time period?
- Is the payment possibly repeated for the same purchase?

Examples:

- Amazon payment of ₹1500 made twice within 5 minutes
- Duplicate UPI payment to the same merchant
- Same bill payment recorded multiple times

## Decision

IF:

- Same merchant
- Similar amount
- Short time difference between transactions

THEN:

Suggest:

- Verify whether the payment was successful once or multiple times
- Check bank statement or merchant confirmation
- Request refund if duplicate payment is confirmed

## Example

User pays:

₹2,000 to Amazon twice within 10 minutes

SpendWise recommendation:

"Possible duplicate transaction detected. Please verify this payment to avoid unnecessary expenses."
# Rule 9: Budget Limit Alert 🚨

## Problem

Users may overspend in certain categories without realizing they are exceeding their planned budget. SpendWise should monitor spending patterns and alert users before they lose control of their expenses.

## Detect

SpendWise should check:

- Has the user set a monthly budget for a category?
- Is the spending approaching or exceeding the budget limit?
- Which categories are contributing to higher spending?

Examples:

- Food budget: ₹5000/month
- Shopping budget: ₹3000/month
- Entertainment budget: ₹2000/month
- Travel budget: ₹5000/month

## Decision

IF:

- Category spending reaches a defined percentage of the budget
- Spending exceeds the set budget limit

THEN:

Suggest:

- Reduce spending in that category
- Review recent purchases
- Adjust budget if required

## Example

User sets:

Shopping Budget: ₹5000/month

Current Spending:

₹4500/month

SpendWise recommendation:

"You have used 90% of your shopping budget. Consider reviewing upcoming purchases to avoid exceeding your monthly limit."
# Rule 10: Spending Pattern Analysis 📊

## Problem

Users may not notice their spending habits and where their money is going. SpendWise should analyze past transactions to identify patterns and provide useful financial insights.

## Detect

SpendWise should check:

- Which categories have the highest spending?
- Are there changes in spending compared to previous months?
- Are there frequent purchases in specific categories?
- Are spending habits increasing or decreasing over time?

Examples:

- Increased food delivery expenses
- Frequent online shopping purchases
- Higher fuel expenses compared to previous months
- Increased entertainment spending

## Decision

IF:

- Spending in a category increases consistently
- A user shows repeated spending patterns

THEN:

Suggest:

- Review spending habits
- Identify unnecessary expenses
- Set category-wise budgets
- Find opportunities to save money

## Example

User spends:

January:
₹3000 on food delivery

February:
₹6000 on food delivery

SpendWise recommendation:

"Your food delivery expenses have increased by 100% compared to last month. Consider reducing frequent orders or setting a monthly limit to improve savings."
# Rule 11: Savings Goal Tracking 🎯

## Problem

Users may have financial goals but may not track their progress regularly. Without monitoring savings, users may fail to achieve their planned goals.

## Detect

SpendWise should check:

- Has the user created a savings goal?
- How much amount has been saved towards the goal?
- Is the user saving regularly?
- Is the current saving rate sufficient to achieve the target?

Examples:

- Emergency fund: ₹1,00,000
- New phone purchase: ₹50,000
- Vacation fund: ₹75,000
- Home renovation: ₹2,00,000

## Decision

IF:

- User has a savings goal
- Current savings progress is below the expected target

THEN:

Suggest:

- Increase monthly savings amount
- Reduce unnecessary expenses
- Set automatic savings reminders
- Track progress regularly

## Example

User sets:

Goal: Buy a new laptop  
Target Amount: ₹80,000  
Target Date: 8 months  

Current Savings:

₹20,000

SpendWise recommendation:

"You have saved ₹20,000 out of your ₹80,000 goal. Save ₹7,500/month to achieve your target within the planned timeline."
# Rule 12: Emergency Fund Monitoring 🛡️

## Problem

Users may not maintain enough savings to handle unexpected financial situations such as medical expenses, job loss, urgent repairs, or emergencies. SpendWise should monitor emergency savings and encourage users to build financial security.

## Detect

SpendWise should check:

- Does the user have an emergency fund?
- What is the user's average monthly essential expense?
- How many months of expenses are covered by current savings?
- Is the emergency fund below the recommended level?

Examples:

- Medical emergencies
- Job transition period
- Home repairs
- Vehicle repairs
- Unexpected expenses

## Decision

IF:

- Emergency savings are below the recommended target
- User has insufficient savings to cover essential expenses

THEN:

Suggest:

- Build an emergency fund gradually
- Save a fixed amount every month
- Reduce unnecessary expenses
- Maintain 3–6 months of essential expenses as a safety buffer

## Example

User's essential expenses:

₹30,000/month

Current emergency savings:

₹40,000

SpendWise recommendation:

"Your emergency fund currently covers around 1.3 months of expenses. Consider increasing savings to build a 3–6 month financial safety buffer."
# Rule 13: Unusual Spending Detection 🚨

## Problem

Users may make unexpected high-value purchases or spend differently from their normal spending pattern. SpendWise should identify unusual transactions and notify users to review them.

## Detect

SpendWise should check:

- Is the transaction amount significantly higher than the user's usual spending?
- Is the purchase outside the user's normal spending pattern?
- Is there a sudden increase in spending frequency?
- Does the transaction occur at an unusual time or category?

Examples:

- Normally spends ₹2,000 on shopping but spends ₹25,000 suddenly
- Unexpected luxury purchase
- Large cash withdrawal
- High-value online transaction

## Decision

IF:

- Transaction amount is higher than the user's normal spending range
- Spending pattern changes significantly

THEN:

Suggest:

- Review the transaction details
- Confirm whether the purchase was intentional
- Check if the expense impacts savings goals or budget

## Example

User's normal shopping expense:

₹3,000/month

New transaction:

₹30,000 electronics purchase

SpendWise recommendation:

"Unusual spending detected. You spent ₹30,000 on electronics, which is significantly higher than your normal shopping pattern. Review this purchase to ensure it aligns with your budget."
# Rule 14: Cash Withdrawal Tracking 💵

## Problem

Cash withdrawals reduce the user's bank balance, but the actual spending purpose is unknown. Without tracking cash usage, SpendWise cannot provide accurate expense insights.

## Detect

SpendWise should check:

- Is the transaction a cash withdrawal?
- How frequently does the user withdraw cash?
- Is the withdrawal amount increasing over time?
- Has the withdrawn cash been categorized or tracked?

Examples:

- ATM Cash Withdrawal
- Bank Counter Withdrawal
- Cash Withdrawal for daily expenses
- Large cash withdrawal

## Decision

IF:

- Money is withdrawn as cash
- Spending details are not available

THEN:

Suggest:

- Add a purpose/category for cash usage
- Track cash expenses manually
- Review frequent cash withdrawals
- Reduce unnecessary cash usage if required

## Example

User withdraws:

₹10,000 from ATM

SpendWise recommendation:

"Cash withdrawal of ₹10,000 detected. Add details about how this cash was spent to maintain accurate expense tracking."
# Rule 15: Debt & Loan Payment Tracking 💳

## Problem

Users may have loans, credit card dues, or other debts that require regular payments. Without tracking these payments, users may underestimate their financial commitments and impact on savings.

## Detect

SpendWise should check:

- Is the transaction related to loan or debt repayment?
- Is there a recurring payment to a bank or lending institution?
- What is the monthly debt repayment amount?
- Is the debt payment increasing or affecting savings?

Examples:

- Home Loan EMI
- Personal Loan EMI
- Car Loan EMI
- Credit Card Bill Payment
- Buy Now Pay Later (BNPL) payments

## Decision

IF:

- Transaction matches loan or debt payment patterns
- Recurring payment is detected

THEN:

Suggest:

- Track monthly debt obligations
- Maintain sufficient balance before due dates
- Avoid unnecessary new debt
- Plan early repayment if financially possible

## Example

User pays:

₹25,000 Home Loan EMI every month

SpendWise recommendation:

"Your monthly loan repayment of ₹25,000 has been detected. Ensure sufficient balance before the due date and monitor debt impact on your monthly savings."
# Rule 16: Bill Payment Reminder 📅

## Problem

Users may forget important recurring payments, which can lead to late fees, service interruptions, or penalties. SpendWise should identify upcoming bills and remind users before the due date.

## Detect

SpendWise should check:

- Are there recurring bill payments?
- Is the payment date consistent every month?
- Has the user paid similar bills previously?
- Are upcoming payments due soon?

Examples:

- Electricity Bill
- Internet Bill
- Mobile Recharge
- Credit Card Bill
- Loan EMI
- Insurance Premium
- Subscription Payments

## Decision

IF:

- A recurring bill payment is detected
- Payment due date is approaching

THEN:

Suggest:

- Pay the bill before the due date
- Maintain sufficient account balance
- Enable automatic payments if required

## Example

User's electricity bill:

₹2,500/month

Due Date:

10th of every month

SpendWise recommendation:

"Your electricity bill payment of approximately ₹2,500 is due soon. Ensure sufficient balance to avoid late payment charges."
# Rule 17: Financial Health Score 📈

## Problem

Users may track individual expenses but may not understand their overall financial condition. SpendWise should analyze income, expenses, savings, and financial habits to provide a simple financial health score.

## Detect

SpendWise should check:

- Income compared to expenses
- Savings percentage
- Debt obligations
- Emergency fund status
- Budget management
- Spending patterns

Examples:

- High savings rate
- Low unnecessary spending
- Controlled debt
- Regular emergency savings

## Decision

IF:

- Financial habits are healthy

THEN:

Increase financial health score and provide positive feedback.

IF:

- Expenses are higher than income
- Savings are low
- Debt burden is high

THEN:

Reduce financial health score and provide improvement suggestions.

## Example

User details:

Monthly Income: ₹70,000  
Monthly Expenses: ₹45,000  
Savings: ₹25,000  
Debt: Low  

SpendWise recommendation:

"Your financial health score is 82/100. You have a good savings rate, but improving emergency savings and controlling unnecessary expenses can further strengthen your financial position."  
# Rule 18: Expense Categorization Accuracy 🏷️

## Problem

Users may have transactions that are difficult to categorize automatically. Incorrect categorization can affect spending analysis, budgets, and financial recommendations.

## Detect

SpendWise should check:

- Does the transaction description clearly indicate a category?
- Is the merchant already mapped to a known category?
- Are similar past transactions available for comparison?
- Is user confirmation required for unclear transactions?

Examples:

- AMAZON → Shopping
- SWIGGY/ZOMATO → Food
- UBER/RAPIDO → Transport
- NETFLIX → Entertainment
- APOLLO PHARMACY → Healthcare

## Decision

IF:

- Merchant or transaction pattern matches a known category

THEN:

Classify automatically.

IF:

- Transaction category is unclear

THEN:

Suggest:

- Ask user to confirm category
- Learn from user corrections
- Improve future categorization accuracy

## Example

Transaction:

"POS 4589 XYZ STORES ₹2500"

SpendWise:

"Transaction category is unclear. Please confirm whether this expense belongs to Grocery, Shopping, or another category."

After user selection:

"Future transactions from XYZ STORES will be categorized automatically."
# Rule 19: Smart Saving Recommendations 💡

## Problem

Users may spend money regularly without realizing possible opportunities to save. SpendWise should analyze spending behavior and suggest practical ways to reduce unnecessary expenses and increase savings.

## Detect

SpendWise should check:

- Are there categories with unnecessary or high spending?
- Are there repeated purchases that can be reduced?
- Are there cheaper alternatives available?
- Is the user spending more than their usual pattern?

Examples:

- Frequent food delivery orders
- Multiple unused subscriptions
- High online shopping expenses
- Expensive recurring services
- Increased entertainment spending

## Decision

IF:

- SpendWise identifies possible savings opportunities

THEN:

Suggest:

- Reduce unnecessary expenses
- Compare cheaper alternatives
- Review recurring payments
- Set spending limits
- Redirect saved money towards savings goals

## Example

User spends:

₹6000/month on food delivery

SpendWise recommendation:

"You spent ₹6000 on food delivery this month. Reducing a few orders or choosing home-cooked meals could help you save approximately ₹2000–₹3000 every month."
# Rule 20: Financial Goal Recommendation 🎯

## Problem

Users may want to achieve financial goals but may not know how much they need to save or how to plan their spending. SpendWise should analyze financial behavior and suggest suitable goals based on income, expenses, and savings capacity.

## Detect

SpendWise should check:

- User's monthly income and expenses
- Current savings amount
- Existing financial commitments
- Available amount for saving
- User's spending patterns

Examples:

- Emergency fund creation
- Vacation planning
- Buying electronics
- Home renovation
- Investment planning
- Long-term savings goals

## Decision

IF:

- User has sufficient saving capacity

THEN:

Suggest:

- Create a financial goal
- Define target amount and timeline
- Allocate monthly savings towards the goal

IF:

- User has low savings capacity

THEN:

Suggest:

- Reduce unnecessary expenses
- Improve saving habits before setting larger goals

## Example

User has:

Monthly Income: ₹70,000  
Monthly Expenses: ₹45,000  
Available Savings: ₹25,000  

SpendWise recommendation:

"You can create a goal of saving ₹1,00,000 in 5 months by allocating ₹20,000 every month towards your target."
# Rule 21: Investment Awareness Recommendation 📈

## Problem

Users may keep their money only in savings accounts and may not be aware of investment options that can help grow their wealth. SpendWise should identify opportunities where users can consider investing based on their financial situation.

## Detect

SpendWise should check:

- Does the user have regular savings after expenses?
- Does the user maintain an emergency fund?
- Is excess money remaining unused for a long period?
- Does the user have existing investments?

Examples:

- Large unused savings balance
- Regular monthly surplus income
- No investment activity
- Low financial goal planning

## Decision

IF:

- User has consistent savings
- Emergency fund is maintained
- Extra funds are available

THEN:

Suggest:

- Explore suitable investment options
- Start goal-based investing
- Learn about different investment products
- Diversify savings based on financial goals

## Example

User has:

Monthly Income: ₹80,000  
Monthly Expenses: ₹45,000  
Monthly Surplus: ₹35,000  

SpendWise recommendation:

"You have a monthly surplus of ₹35,000 after expenses. Consider exploring investment options aligned with your financial goals to help grow your savings over time."
# Rule 22: Financial Anomaly Detection 🔍

## Problem

Users may experience unexpected changes in their financial activity, such as sudden large expenses, unusual income, or abnormal transaction behavior. SpendWise should identify these changes and alert users.

## Detect

SpendWise should check:

- Are there transactions significantly different from normal patterns?
- Is there a sudden increase or decrease in spending?
- Is there an unusual income or withdrawal activity?

Examples:

- Sudden ₹50,000 purchase
- Unexpected large cash withdrawal
- Income received earlier or later than usual

## Decision

IF:

- Transaction behavior differs significantly from normal patterns

THEN:

Suggest:

- Review unusual transactions
- Verify payment details
- Check impact on budget and savings

## Example

User normally spends ₹30,000/month but spends ₹80,000 this month.

SpendWise recommendation:

"Unusual financial activity detected. Your spending has increased significantly compared to previous months. Review recent transactions to understand the reason."
# Rule 23: Merchant Spending Analysis 🏪

## Problem

Users may spend repeatedly with the same merchants without realizing the total amount spent. SpendWise should analyze merchant-wise spending to provide better insights.

## Detect

SpendWise should check:

- Which merchants receive the highest payments?
- How frequently does the user transact with a merchant?
- Total monthly spending with each merchant?

Examples:

- Amazon
- Swiggy
- Uber
- Flipkart
- Myntra

## Decision

IF:

- Spending with a merchant is frequent or increasing

THEN:

Suggest:

- Review spending with that merchant
- Compare alternatives
- Reduce unnecessary purchases

## Example

User spends:

₹12,000/month on Amazon

SpendWise recommendation:

"You spent ₹12,000 on Amazon this month. Review your purchases and identify items that can be postponed or avoided."

# Rule 24: Expense Trend Prediction 📈

## Problem

Users may not know how their future expenses will look based on current spending habits. SpendWise should predict upcoming spending trends.

## Detect

SpendWise should check:

- Previous months' spending patterns
- Category-wise expense growth
- Seasonal spending behavior

Examples:

- Increased travel expenses
- Festival shopping trends
- Rising food expenses

## Decision

IF:

- A category shows continuous growth

THEN:

Suggest:

- Prepare for higher future expenses
- Adjust budget
- Reduce unnecessary spending

## Example

Food expenses increased:

January: ₹4000  
February: ₹6000  
March: ₹8000  

SpendWise recommendation:

"Your food expenses are increasing every month. Consider setting a monthly limit to control spending."
# Rule 25: Monthly Financial Report Generation 📊

## Problem

Users may find it difficult to understand their complete financial activity. SpendWise should generate simple monthly reports.

## Detect

SpendWise should analyze:

- Total income
- Total expenses
- Savings
- Highest spending categories
- Budget performance

Examples:

- Monthly summary
- Category breakdown
- Savings progress

## Decision

IF:

- Monthly transaction data is available

THEN:

Generate:

- Income summary
- Expense report
- Savings analysis
- Improvement suggestions

## Example

Monthly Report:

Income: ₹70,000  
Expenses: ₹45,000  
Savings: ₹25,000  

SpendWise recommendation:

"You saved 35% of your income this month. Your highest expense category was shopping."
# Rule 26: Savings Rate Calculation 💰

## Problem

Users may not know how much of their income they are saving. SpendWise should calculate savings percentage and track improvement.

## Detect

SpendWise should check:

- Monthly income
- Monthly expenses
- Remaining savings amount

Formula:

Savings Rate = (Savings / Income) × 100

## Decision

IF:

- Savings rate is calculated

THEN:

Suggest:

- Improve savings percentage
- Maintain healthy spending habits
- Set savings targets

## Example

Income:

₹70,000

Savings:

₹20,000

Savings Rate:

28%

SpendWise recommendation:

"Your savings rate is 28%. Increasing it gradually can help you achieve financial goals faster."
# Rule 27: Needs vs Wants Detection ⚖️

## Problem

Users may spend money on non-essential items without understanding the impact on savings. SpendWise should help differentiate necessary expenses from optional spending.

## Detect

SpendWise should check:

- Is the transaction essential or optional?
- Does the purchase support basic needs or lifestyle choices?

Examples:

Needs:
- Rent
- Groceries
- Medical expenses

Wants:
- Luxury shopping
- Premium subscriptions
- Unplanned purchases

## Decision

IF:

- Transaction is identified as a non-essential expense

THEN:

Suggest:

- Review purchase necessity
- Delay non-essential purchases
- Prioritize financial goals

## Example

User buys:

₹15,000 luxury watch

SpendWise recommendation:

"This purchase is categorized as a want. Review whether it aligns with your current savings goals."
# Rule 28: Lifestyle Inflation Detection 🚨

## Problem

Users may increase their spending as their income grows, reducing their ability to save. SpendWise should identify lifestyle inflation patterns.

## Detect

SpendWise should check:

- Income growth compared to expense growth
- Increase in luxury or discretionary spending
- Changes in spending habits after salary increase

Examples:

- Higher restaurant spending after promotion
- More expensive subscriptions
- Increased shopping frequency

## Decision

IF:

- Expenses increase faster than savings after income growth

THEN:

Suggest:

- Maintain spending discipline
- Increase savings with income growth
- Review unnecessary lifestyle upgrades

## Example

Salary increased:

₹60,000 → ₹80,000

Expenses increased:

₹40,000 → ₹70,000

SpendWise recommendation:

"Your income increased, but expenses increased significantly. Consider saving a portion of your additional income."
# Rule 29: Payment Due Date Prediction 📅

## Problem

Users may miss recurring payments because they forget due dates. SpendWise should predict upcoming payments based on past transactions.

## Detect

SpendWise should check:

- Previous payment dates
- Recurring transaction patterns
- Upcoming expected payments

Examples:

- EMI
- Credit card bill
- Insurance premium
- Utility bills

## Decision

IF:

- Recurring payment pattern is identified

THEN:

Suggest:

- Set reminders
- Maintain sufficient balance
- Enable auto-payment if required

## Example

Credit card payment usually happens on the 15th.

SpendWise recommendation:

"Your credit card payment is expected around 15th of this month. Ensure sufficient balance before the due date."
# Rule 30: Personalized Financial Advice 🤖

## Problem

Every user's financial situation is different. SpendWise should provide personalized suggestions based on income, expenses, goals, and spending behavior.

## Detect

SpendWise should analyze:

- Income pattern
- Spending categories
- Savings habits
- Financial goals
- Debt obligations

Examples:

- Low savings
- High shopping expenses
- Increasing debt
- Good saving habits

## Decision

IF:

- User financial patterns are analyzed

THEN:

Provide:

- Personalized saving suggestions
- Spending improvement tips
- Goal-based recommendations

## Example

User spends heavily on shopping and has low savings.

SpendWise recommendation:

"Your shopping expenses are higher than your savings capacity. Reducing non-essential purchases by ₹3000/month can help you achieve your savings goal faster."
