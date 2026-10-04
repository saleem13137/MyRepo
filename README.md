Basics of Shell scripting 

As discussed, the TRS in the original ET transaction is calculated internally by Murex based on the ET feed, and therefore can have a small difference compared to the TRS stored in ET and subsequently passed to Hub.
For the reversal transaction, the TRS received from Hub may therefore be slightly different from the TRS of the original deal in Murex. This is a known and expected difference in the existing ET/Murex pricing flow and is not specific to the reversal process.
The difference observed is minor and should be acceptable from the FX Desk perspective.
Please confirm if the Desk is okay with accepting this minor TRS difference so that we can proceed with promoting the fix to Production in the upcoming release.
