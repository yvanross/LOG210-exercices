## Bank Automated Teller Machine (ATM)


ATM is initially turned off. After the power is turned on, ATM performs
startup action and enters Self Test state. If the test fails, ATM goes
into Out of Service state, otherwise there is triggerless transition to
the Idle state. In this state ATM waits for customer interaction.

The ATM state changes from Idle to Serving Customer when the customer
inserts banking or credit card in the ATM\'s card reader. On entering
the Serving Customer state, the entry action readCard is performed.
Note, that transition from Serving Customer state back to the Idle state
could be triggered bycancel event as the customer could cancel
transaction at any time.

![](/assets/exercices.gddoc.docx/image20.png){width="6.5in" height="5.236111111111111in"}
