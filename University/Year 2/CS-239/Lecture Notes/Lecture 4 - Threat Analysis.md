#### Impact Rating:
Impact is rated on four main categories
- Safety
- Financial
- Operational
- Privacy

#### Vehicle Network Technologies:
- In-vehicle network:
	- CAN and CAN-FD
	- FlexRay
	- Automotive Ethernet
	- LIN

- External Vehicle Connectivity
	- Cellular
	- Wifi
	- Bluetooth
	- DSRC
	- OBD-II
	- EV Charging

- Vehicle Attack Surfave:
	- Attacks via offboard systems
	- Attacks on wireless interfaces
	- Attacks on wired inrerfaces
	- Direct attacks on vehicle network
	- Attacks on ECUs

#### Automotive Cybersecurity Regulations and Standards:
- New UNECE regulations and standards place new requirements on vehicle manufacturers and the supply chain to implement and demonstrate best practice in cybersecurity.

#### Threat Analysis & Risk Assessment  in ISO/SAE 21434
- Risk-based approach to establishing cybersecurity requirements.
	- Threat Analysis
		- Asset Identification
		- Thread Scenario Identification
		- Attack Path Analysis
	- Risk Assessment
		- Impact Rating
		- Attack Feasibility Rate
		- Risk Value Determination
	- Cybersecurity Goals
		- Risk Treatment Decision
- Output is a measure of the risk associated with the unwanted event
- Risk treatment option are decided and cybersecurity goals defined

#### TARA During the Concept Phase
- TARA - Threat Analysis and Risk Assessment
- Asset Identification -> Threat Scenario Identification -> Impact Rating -> Attack Path Analysis -> Attack Feasability Rating -> Risk Determination -> Risk Treatment Decision

#### Pre-Requisites for performing a TARA:
- ISO/SAE 21434 Clause 9.3 requires an item definition, which identifies the following information about the item:
	- Item boundary
	- Interfaces internal or external to the vehicle
	- Item functions
	- Preliminary architecture
	- Information about the operational environment
	- Assumptions relevant to cybersecurity
- The infroamtion required is similar to that required by ISO 26262 for Functional Safety
- In Addition:
	- The item may be defined differently for cybersecurity and functional safety (different components in scope)
	- More architectural information might be needed (E.G: Data flows, relationship between functions and data)
	- Additional cybersecurity relevant information can be included (known threats and vulnerabilities).

#### Bowtie Model:
![[Pasted image 20250308151934.png]]

#### Threat Analysis - General Approach
- Asset Identification - Identify assets to protect, focusing on the consequences.
	- WHAT assets may be targeted and what damage may occur?
	- WHO are the potential attackers and stakeholders
	- WHY might they target the assets?

- Threat Modelling - Determine the threats to those assets and how an attaker might realise those threats.
	- WHERE in the system might the attacker target
	- WHEN in the vehicle lifecycle might the threat be realised
	- HOW might an attacker realise the threat

- A systematic approach that considers how an attacker might attack the system and how the system stakeholders are impacted, including:
	- Consideration of "Dark Side Scenarios" - EVITA
	- STRIDE analysis - Microsoft
	- Attack Trees
![[Pasted image 20250308152337.png]]

#### Important Definitions:
- Asset
	- Object that has value, or contributes to value
- Cybersecurity Property:
	- Attribute that can be worth protecting
- Damage Scenario
	- Adverse consequence involving a vehicle or vehicle function and affecting a road user.

#### Damage Scenarios:
- Identify cybersecurity properties of the assets that:
	- A stakeholder might want to protect
	- An attacker might want to compromise

- Identify damage scenarios that could result from the assets being compromised and satisfy the attacker motivations
	- Involve a vehicle or vehicle function
	- Lead to an adverse consequence affecting multiple victims (stakeholders)

- The aim is to identify valid "triples" of (asset, cybersecurity property, damage scenario).
	- An asset is only an asset if a compromise to one of its cybersecurity properties can lead to a damage scenario
	- A damage scenario is only a damage scenario if it can result from a compromise of a cybersecurity property of an asset

#### Linking Assets to Damage Scenarios:
- The damage scenario should describe the casual chain
	-  From the compromise of the cybersecurity property to the asset 
	- To the consequence experienced by the stakeholder
![[Pasted image 20250308153001.png]]

#### Threat Modelling - Threat Scenarios
- Threat Scenario:
	- Potential cause of compromise of cybersecurity properties of one or more assets in order to realise a damage scenario

Things to consider:
- Where the asset is involved in the system? 
	- ECUs
	- Connections between ECUs
	- Interfaces to other items

- High-level architectural elements
	- Modules with external connectivity
	- Gateways
	- In-vehice network type (CAN, Ethernet)

- How might an attacker compromise a cybersecurity property of an asset to achieve a damage scenario
	- Ways in which the cybersecurity properties of an asset could be compromised
		- Spoofing / Tampering
		- Information Disclosure
		- Denial of Service
		- Elevation of Privilege
	- Potential Attackers
		- Criminal
		- Mechanic
		- Driver / Owner

#### Data Flow Diagrams
- WHERE in the system might an adversary attack
- Construct a high-level model of the item based on the item definition
	- E.G: UML data flow diagram (DFD)
![[Pasted image 20250308153522.png]]

#### Threat Modelling - STRIDE:
- HOW might a cybersecurity property of an asset be compromised?
- Systematic analysis of each element of the DFD
- use STRIDE to identify threat scenarios

- S - Spoofing
	- A person or entity masquerading as another
- T - Tampering
	- Insertion, modification or deletion of data
- R - Repudiation
	- An entity denies responsibility for an action
- I - Information Disclosure
	- Provision or leak of information to an unauthorised entity
- D - Denial of Service
	- Making a resource unavailable to authorised entities
- E - Elevation of privilege
	- An entity gains greater authorisation than permitted

- Different types of attack are applicable to different DFD elements:
	- Processes - STRIDE
	- Dataflows - TID
	- External Entities - SR
	- Data Stores - TRID

#### Damage Scenarios - What to Consider? 
- Situation - A remote attack via the cellular or wifi interface enables injection of CAN messages to control steering and braking
- Consider the assets, potential attacker(s), motivations and damage resulting from a successful attack
	- What is the casual chain from the compromise of the asset to the adverse consequences
	- Does the compromised asset affect a vehicle function?
	- What is the adverse consequence and what is the attacker trying to achieve?
	- Who are the affected stakeholders? 

#### Attack Paths:
- Attack paths:
	- Represent the actions that could be taken by an attacker to realise a threat scenario
	- In the concept phase, these are likely to be high level but can be further elaborated in later stages of the design
- In the below example, two attack paths could be used to spoof CAN messages are developed:
	- AP01, inject CAN messages by remove compromise of infotainment system
	- AP02, inject CAN messages by direct connection to CAN
- Note that the same two attack paths can be used to realise both treat scenarios TS01 and TS02

