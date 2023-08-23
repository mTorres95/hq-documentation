---
title: "Payroll Associates"
date: 2023-05-30T12:08:59-03:00
---

## Where to find it

* Builder: Management > Payroll > Payroll Associate
* Runtime: On a nested view for each Payroll Run

## Description

This records are created on the 21st of every month > Listener "**Generate payroll run from pending compensations**".

## Tips

This record has it's own Status and has fields that have other status. Pay attention to not mix them up.

## Fields

* **Associate**: The person that works for Slingr that's being paid (Relationshipt to sys>users)

* **Area**: The user's area (Frontend, Platform, Marketing, etc.)

* **Payroll Run**: Relationship to the payroll run record that created this payroll associates. 

* **Compensations**: Relationship to Management>Payroll>Compensations, those that match the associate and that have *pending* status. If no compensation is found, the payroll associate is not created and the user is put on the list of "Associates Not Included" in the payroll".

* **Total amount**: The sum of the amount of every compensation per payroll associate.

* **Payment Document**:
	* **Authorization Document**: Relationship to Management>Contracts. This is the payment document sent to the user where they can indicate they preferred payment method for each month.
	* **Sent Day**: When the document was sent. This is useful for R2-D2's notifications.
	* **Error Message**

* **Status**:  
	* ***Pending*** means the payroll has been created and the default status of the payroll associates is pending, not action has yet been performed. 
	* ***Document Sent***
	* ***Document Failed*** 
	* ***Ready To Pay*** means the associate has completed the payment document and HQ has the information about how they want to receive their amount.
	* ***Paid*** simply means the payment has been completed. It's also used but the "Prepare crypto batch" action to not repeat associates.
	* ***Discarded***

* **USDC**: One of the three possible method of payments.
* **US Account**: One of the three possible method of payments.
* **Payoneer**: One of the three possible method of payments.

#### Method of payment
The last three fields reflect the chosen method of payment the user indicated in their payment document. All three of them include **Amount** and **Status** (this status can be Not Selected, Ready to Pay or Paid).

* *USDC*: Also includes the wallet address where to send the money and the transaction information to follow the payment, indicating the **status** of that transaction (that can be Submitted, Confirmed, Error or Retrying).

* *US Account*: Also includes the Routing number, account, bank name and address to know to which bank account the money must be sent.

* *Payoneer*: Also includes the user's email, that is enough to identify the user's Payoneer account.

