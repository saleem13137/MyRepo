Basics of Shell scripting 

SWIFT MT202 Pending in PFU/Fircosoft Queue – Troubleshooting Guide
Overview
This document explains the troubleshooting steps when SWIFT payment messages (MT202) remain in Sent status in Murex and ACK is not received.
Payment Flow
Plain text
Murex → BMG/SMG → PFU/Fircosoft → SWIFT → ACK → Murex
Issue Symptoms
Back-office reports payment status stuck in “Sent”
No ACK received in Murex
Payment not visible in SWIFT queue
Transactions pending in PFU/Fircosoft queue
Troubleshooting Steps
1. Verify MT202 Generated from Murex
Check:
Payment instruction generated successfully
MT202 created
Status = Sent
If MT202 is not generated → Check Murex issue.
2. Verify Message Sent to BMG/SMG
Check middleware logs to confirm:
Message transmitted successfully
No queue or routing issue
If not received by BMG/SMG → Raise with middleware team.
3. Check with SWIFT Team
Confirm:
Any pending outbound messages?
Any SWIFT gateway issue?
Is transaction visible in SWIFT queue?
If SWIFT team cannot see the transaction, proceed to PFU check.
4. Check PFU/Fircosoft Queue
Coordinate with PFU team to verify:
Transaction pending in screening queue
Any sanction/manual review hold
Any processing backlog
5. Resolution
PFU team should:
Clear/release transaction
Forward payment to SWIFT
Post release:
SWIFT ACK should be received
Murex status should update from Sent → ACK
Key Observation
If:
Murex generated MT202 successfully
SWIFT team cannot see the message
ACK not received
Then likely issue area is:
➡ PFU/Fircosoft screening queue.
Teams Involved
Team
Responsibility
Back Office
Report issue
Murex Support
Verify payment generation
Middleware Team
Verify BMG/SMG routing
SWIFT Team
Verify SWIFT gateway
PFU Team
Verify screening queue
Quick Reference Flow
Plain text
Murex Generated?
   ↓ Yes
Sent to BMG/SMG?
   ↓ Yes
Visible in SWIFT?
   ↓ No
Check PFU/Fircosoft Queue
   ↓
Release Transaction
   ↓
Receive ACK
