✅ User Story 1: Trade Reception from Bloomberg
User Story
As a treasury trader, when I book an FX trade in Bloomberg, I want the trade to be received in Murex so that it can be processed further.
Acceptance Criteria
Trade booked in Bloomberg is received in Murex via the interface in near real-time
Trade payload contains client rate and all required trade details
Trade is received in Murex staging/interface layer successfully
Trade is not auto-booked in Murex
Each trade is uniquely identified using Bloomberg Deal ID
Any interface or parsing errors are logged and traceable


✅ User Story 2: Routing Trade to OSP for Manual Action
User Story
As a treasury sales user, I want all trades received from Bloomberg in Murex to be routed to OSP so that I can review and complete required details before booking.
Acceptance Criteria
All incoming Bloomberg trades are routed to OSP before booking in Murex
Trade is created in OSP with Bloomberg Deal ID as reference
Trade status is set to “Pending Manual Action”
Client rate received from Bloomberg is displayed as read-only
Any treasury rate coming from Bloomberg (including comments/free text) is not considered reliable and is ignored
No trade is booked in Murex while it is pending in OSP
Duplicate trades are prevented
Audit trail is maintained for trade receipt and routing


✅ User Story 3: Treasury Rate Validation in OSP
User Story
As a treasury sales user, I want to input and validate the treasury rate on trades in OSP so that the correct rates are used before booking.
Acceptance Criteria
User can view trades in “Pending Manual Action” status
Treasury rate (TRS) field is mandatory for user input
System does not rely on treasury rate from Bloomberg (if present)
System validates treasury rate for format, precision, and basic tolerance checks
System calculates and displays margin = client rate – treasury rate
Trade cannot proceed without valid treasury rate
On successful validation, trade status is updated to “Ready for Processing”
Audit trail captures user input and changes to treasury rate


✅ User Story 4: Booking Trade in Murex with Validated Rates
User Story
As a treasury system user, I want trades validated in OSP to be booked in Murex using the treasury rate from OSP and client rate from Bloomberg so that correct P&L and trade details are captured.
Acceptance Criteria
Only trades marked “Ready for Processing” are picked from OSP
Transformation logic uses:
Client rate from Bloomberg
Treasury rate from OSP
Margin is derived as part of the process (client rate – treasury rate)
Trade is booked in Murex with correct client rate, treasury rate, and derived margin
Trade is successfully validated and booked in Murex
Trade status in OSP is updated to “Booked” after success
Failed trades move to “Error” status with proper logs
Duplicate booking is prevented using Deal ID
Full traceability is maintained between Bloomberg, OSP, and Murex
