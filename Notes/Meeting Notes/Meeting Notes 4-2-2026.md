[[Initial Notes]]

Separate Epics made for the Didit Implementation
	Made the wallet a separate module to allow for app-wide integration
	Didit implementation is simply made for demos without the full implementation with the wallet integration
	Making manual requests to us to make workflows while having a defined list of workflows will be the way forward
	More research required to having the same data saved at didit and our db for performance 
	More research required on allowing time barred access to sessions to clients

Separate Wallet Module
	Wallet can be enabled for Tenant
	Currency and Region can be custom (with a default selected at the start)
	Card payment via Debit/Credit Card to Top-up (Bank transfer not included for ease of development)
	Invoicing can be included in Pricing for App-Wide functionality to allow for 2 step payments
	Approval system can be implemented for Payment system used for certain transactions (external sites)
	Audit system with which users initiated payments are logged to allow for control 
	Auto-detection for suspicious activity
	Auto Top-up based on set thresholds
	Auto-Statement via email and Dashboard for account
	Failed Transaction handling to allow for reliability
	Freeze or Unfreeze wallet to prevent unauthorized payments

Further research will be done on both features when implementation is done later

Wallet cannot be imported from premade sources
	AI can be used to expedite development time
	But exact requirements is the major blocker

Priority for features is also important for Wallet
	Can leave dashboard out
	Freezing functionality too

Estimated time for Didit demo is 2.5 - 3 weeks (Sami)

Final decision will be done tmrw by Boss

Payment Plan required for all workflows
	Essential for pricing
	Will be needed for double entry of payment

Making a separate platform for Didit as White Label Platform
	Better to do so from the start as 75% of work will have to repeated if done Remindoo First and then Remade later
	Separate Platform will be made with integration with Remindoo
	Wallets for each platform will have to be made separately
	Remindoo users will have to be treated separately from outside users
	Wallet can be foregone if payments are done directly with every use, but this approach is better for development time but bad for UX (Suggested for Demo, while a month is taken for development of wallet)
	Card details can be saved in the system to remake requests (might be possible to not need manual authentication every time)


Stress Testing
	Create virtual users to check if the backend can handle various levels of load associated with differing numbers of users
	Will require separate tests for each function of the app
	Not feasible for AI to create tests (can be used to replicate for similar tests)
	Will have to create a list of functions and rank them by importance to prioritize the ones that are the most in use
	*Do the ones that will be most in use instead of doing all of them*
	Weightage for Load is 70% Number of Employees and 30% Number of Clients
	*Task Timers
	Service Template Creation No
	Clients Creation No
	Automated Features
	Emails
	Leads No*
	*Use a week for stress testing*
	*Ascertain the amount of load in in-house use* by using the amount of requests per period on supabase
	*We supplement the lack of adequate stress testing by increasing the amount of resources on supabase*
	Additionally, we can set up for a quick turnaround in case of situations of major module failure to show a "technical difficulties, please wait patiently" screen

*Research Outlook implementation* (given to Sami)

*As an end user,
	Performance is secondary to features. Features that are useful are worth suffering through mediocre or slightly bad performance*

*Research XML HMRC APIS* (given to Sami)

*Sample stress testing for a week and then, spend the rest of the time working on the rest of the features*

Forwarding emails is not working bugfree, among other bugs

*Give the email module for inhouse use for proper testing*

OpenAI Keys need to be entered for each tenant (need bubble frontend)

*Leave Stress Testing until planning is done for the rest of the month after research*

*We also need to create a superadmin system to give us access to an external tenant* and also for things like the workflow creation frontend for didit.

*XML, Outlook, Adsum, OpenAI API Keys* (Sami Stuff)

Email integration tmrw, XML the day after

*Reference Number and other relevant info, Adsum Liabilities, add link for payment to HMRC in Client Portal* (For Aftab)

*Have to create FE for Leads and Proposals dashboard* (for Me)
