Readme file
Subject: MRRE – UPI not updated for Near Leg of FX Swap trades (Anna DSB integration)
Environment:
[UAT / PROD – specify]
MRRE Interface: Java-based (Unix deployment)
Integration: Murex ↔ ANNA DSB (UPI retrieval)
Issue Summary:
For FX Swap trades, the UPI (Unique Product Identifier) is not getting populated for the near leg trade, while it is successfully updated for the far leg trade.
Expected Behavior:
Both legs of the FX Swap (near and far) should receive and update the UPI in the designated UDF field in Murex after MRRE processing.
Actual Behavior:
Trade 1 (Near Leg):
UPI not updated in UDF
No update event observed from MRRE (or specify if partially observed)
Trade 2 (Far Leg):
UPI successfully fetched from ANNA DSB
UDF updated correctly in Murex
Flow Description:
FX Swap trade is booked in Murex (2 legs generated: near & far)
Trade event notification sent to MRRE interface
MRRE calls ANNA DSB to fetch UPI
MRRE sends update event back to Murex with UPI
Observation:
MRRE appears to process only one leg (far leg) for UPI enrichment
Near leg is either:
Not being picked up by MRRE, OR
Filtered/ignored during processing, OR
Failing during UPI retrieval/update
Impact:
Incomplete regulatory enrichment (UPI missing for near leg)
Potential reporting / compliance issues
Request to Murex:
Confirm whether MRRE is designed to process both legs of FX Swap trades
Check if any product-type / leg-level filtering logic exists
Validate if near leg qualifies for UPI generation as per ANNA DSB rules
Assist in identifying why near leg is not triggering / completing MRRE flow
Provide logs/debug steps to trace trade-level processing in MRRE
