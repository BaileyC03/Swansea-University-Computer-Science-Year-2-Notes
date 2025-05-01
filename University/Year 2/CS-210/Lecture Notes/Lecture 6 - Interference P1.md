#### Shared Resources: Mutual Exclusion
- Imagine 2 users sharing a printer
	- USER = (acquire -> use -> release -> USER)
	- PRINTER = (acquire -> release -> PRINTER)
- You want to look for things you can control or own.
	- If you can do this, it's likely a resource which may be shared.

#### PROCESS SHARING:
{a1, ..., an} :: P
- Replaces every action label 'label' in the alphabet of P with the labels a1.label, ..., an.label.
- Further, every transition label (label -> Q) in the definition of P is replaced by the transitions ({a1.label, a2.label, ..., an.label} -> X)
- When you composite, the action becomes the same (resulting in fewer states)

#### ACTION SYNCHRONISATION:
- Consider the following:
	- When client wants data from server it:
		- Calls for data
		- Waits for reply from server
		- after recieving data, continues to be client.
	- While server:
		- Retrieves the data and sends them in reply.
- The issue with this is the server depends on the client so there is a specific order but the order is split between the 2 processes.

#### ACTION RELABELLING:
- Relabelling functions are aplied to processes to change the names of action labels.
- General form of relabelling function:
		/{newLabel1 / oldLabel1, ..., newLabelN/oldLabelN}
- E.G:
		||CLIENT_SERVER = (CLIENT || SERVER) /{call/recieve, ..., wait/reply}.
- We can use action relabelling to synchronise the actions "use" and "print" however we have to do that for all instances and is henceforth a pain in the ass.

#### ACTION HIDING:
- Sometimes we have actions that are local and unimportant from analysis perspective. We can hide them as such:
-  Minimise Operator '\'
	- When applied to process P, the hiding operator \\{a1,..., an} replaces the actions a1, ..., an from the alphabet of P with concealed actions represented as **tau**. They're "silent" actions.
- Interface operator '@'
	- When applied to process P, the interface operator @(a1,...,an) removes the actions a1, ..., ax from the alphabet P.

#### ORNAMENTAL GARDEN PROBLEM:
- Two turnstiles (west and east) allow people to enter the garden
-  The turnstiles run concurrently and share a single counter which increment 100 times each
- Consider how to make an object oriented program for this