
As a TSY Sales user,
I want all FX Swap trades and Forward trades (above spot) executed via Direct Dealing and OBO channels to be automatically booked in Murex.

The enhancement should cover:
FX Swap Trades
All FX Swap trades executed via:
Direct Dealing
OBO (On Behalf Of)
Must be automatically captured and booked in Murex.
Forward Trades (Above Spot)
All Forward trades (tenor > spot) executed via:
Direct Dealing
OBO
Must be automatically booked in Murex

1. Auto Booking of FX Swap Trades
Given an FX Swap trade is successfully executed via Direct Dealing or OBO
When the trade is confirmed in the front-office platform
Then the trade should be automatically captured and booked in Murex within the defined SLA
✅ 2. Auto Booking of Forward Trades (Above Spot)
Given a Forward trade (tenor greater than spot) is executed via Direct Dealing or OBO
When the trade is confirmed
Then the trade should be automatically booked in Murex with correct product classification as Forward


As a TSY Sales / Risk Control user,
I want the system to perform both Customer Limit Check and Liquidity Provider (LP) Limit Check for all FX trades executed via Direct Dealing and OBO,
So that trades are only executed and booked when both limits are successfully validated, ensuring proper risk control and compliance.
🧩 Scope of Enhancement
Applicable for:
FX Swaps
Forward trades (above spot)
Channels:
Direct Dealing
OBO (On Behalf Of)
⚙️ Key Requirement
Introduce an additional LP limit validation alongside existing customer limit check
Trade should proceed only if BOTH checks pass
If any check fails:
Trade must be rejected
No booking should happen in Murex
🟢 Acceptance Criteria
✅ 1. Customer Limit Check
Given a trade is initiated via Direct Dealing or OBO
When the system performs limit validation
Then the existing customer limit check must be executed
✅ 2. LP Limit Check
Given a trade is initiated
When the system processes the trade
Then an additional Liquidity Provider (LP) limit check must be performed
✅ 3. Successful Dual Validation
Given both Customer Limit and LP Limit checks are successful
When the trade is confirmed
Then:
The trade should proceed
The trade should be auto-booked in Murex
