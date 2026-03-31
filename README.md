# MyRepo

🟠 1. Issue / Summary
Mismatch observed between indicative transfer amount displayed on the initial (entry) screen and the final amount shown on the review/confirmation screen for GVGT transfers.
The initial screen displays an amount calculated using indicative board rates sourced from HUB (via Murex/RTDS), whereas the review screen displays an amount calculated using real-time executable FX rates retrieved from ET (via TRAPI RFQ). This results in a visible difference in the transfer amount presented to the user.
🟢 2. Resolution
The discrepancy was analyzed and confirmed to be due to different pricing sources used across the transaction journey:
The initial screen uses static/periodic board rates (refreshed ~4 times daily from HUB).
The review/confirmation screen uses real-time RFQ-based executable rates from ET.
ET logs confirm:
No RFQ was triggered during the initial screen load.
RFQ and Deal Decision were triggered only during confirmation.
The same rate was consistently used within ET for execution.
This confirms that:
ET pricing is functioning correctly and consistently.
The difference arises due to channel usage of indicative vs executable rates, not due to any pricing inconsistency or recalculation issue within ET.
🔵 3. Overall Description (for Jira Notes / Closure Comments)
The issue was caused by the use of two different FX rate sources within the same transaction flow. The indicative amount shown on the entry screen is derived from periodically refreshed board rates (HUB/Murex), while the final transaction amount is calculated using real-time executable rates from ET during confirmation.
Since board rates are not real-time and not guaranteed for execution, a variance between indicative and actual amounts is expected. ET correctly maintains rate consistency between RFQ and Deal Decision using the same transaction key, and no discrepancy was observed in ET pricing.
The behavior is therefore by design, but may lead to customer confusion due to lack of alignment between indicative and executable pricing.
