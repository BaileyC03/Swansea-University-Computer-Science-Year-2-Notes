#### Introuction
- ISO/SAE 21434 requires us to determine a risk "value" associated with each threat scenario.
- In general, risk is assessed by considering:
	- The impact of the unwanted event if it occurs
	- The likelihood of the unwanted event
- However, "Probability" and "Likelihood" arent great terms for cybersecurity as cybersec is dealing with adaptive human adversaries.
- Threat scenarios are classified by considering a qualitative assessment of the risk associated with a successful attack

- In ISO/SAE 21434, risk is determined for a threat scenario as a combination of:
	- Impact rating of the associated damage scenarios
	- Attack feasability rating 
		- this is our substitute for likelihood

#### Impact Rating:
- Impact of each damage scenario is rated in 4 categories:
	- Safety
		- Attack causes a hazard with potential for physical harm
	- Financial
		- Attack leads to financial loss
	- Operational
		- Attack leads to performance degradation or inconvenience
	- Privacy
		- Attack leads to a compromise of personal data
- Impact rating considers the potential damage of harm to road users including:
	- Drivers, Passengers and other road users

- Other stakeholders to be considered: 
	- Civil authorities, Fleet operators ETC
	- Vehicle manufacturers and component suppliers

- If additional stakeholders are considered, then corresponding additional impact categories should be added

#### Impact Rating:

| Impact Rating | Safety Impact Criteria                                             | Financial Impact Criteria                                                                                       | Operational Impact Criteria                                                             | Privacy Impact Criteria                                                                                                  |     |
| ------------- | ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | --- |
| Severe        | Life threatening injuries, fatal injuries                          | Leads to catastrophic consequences in which the affected road user may never overcome                           | The operational damage leads to the loss or impairment to a core vehicle function       | Leads to significant or irreversible impact to the road user. Highly sensitive info and easy to link to an individual    |     |
| Major         | Severe and life threatening injuries in which survival is probable | Leads to substantial consequences in which the affected road user will be able to overcome                      | The operational damage leads to the loss or impairment of an important vehicle function | Either highly sensitive and hard to link to an individual or sensitive and easy to link to an individual                 |     |
| Moderate      | Light and moderate injuries                                        | Leads to inconvenient consequences which the affected road user will be able to overcome with limited resources | The operational damage leads to a partial degradation of a vehicle function             | Leads to inconvenient consequences to the road user. Either sensitive but hard to link or non-sensitive and easy to link |     |
| Negligible    | No injuries                                                        | No effect, negligible consequences or is irrelevant to the road user                                            | Leads to no impairment or non-percieveable impairment of a vehicle function             | No effect or negligible consequences                                                                                     |     |
#### Attack Feasibility Rating: 
- Proxy for likelihood
- 3 approaches to determine:
	- Attack Potential
	- CVSS
	- Attack Vector
- Increasing attack effort and attack feasability are negatively corrolated

#### Attack Potential Based approach:
- Indicates the cost or difficulty of a successful attack
- Based on 5 factors:
	- Elapsed Time
	- Expertise needed
	- Knowledge of an item or component needed
	- Window of opportunity
	- Equipment needed
- You add points from each category to come up with a total.
![[Pasted image 20250309131856.png]]

#### Elapsed Time:
- Consider the total time for all steps of the attack
	- Identifying Vulnerabilities
	- Development of exploits
	- Carrying out the exploit

#### Expertise:
- Considers the amount of expertise needed by the attacker to carry out the attack path
	- Select the maximum level of expertise considering all levels of the attack
	- Includes expertise needed to understand the item/component, identifying vulnerabilities, developing exploits and carrying out exploits.
	- "Multiple Experts" Should be for paths that need 2 different fields of expertise

#### Knowledge of Item or Component:
- Knowledge considers the level of detailed information about the item or component needed by the attacker to carry out the attack path
- Select the maximum level of knowledge considering ALL steps of the attack.
- This factor can usually be "traded" for time or expertise
	- Experts know their shit
	- Time taken to reverse engineer
- If other factors allow for time or experts to discover the required knowledge, this can be set to public

#### Window of Opportunity:
- Window of opportunity considers the type of access to the item or component needed by the attacker to carry out the attack path
	- Can be considered related to the attack vector:
		- Unlimited -> Remote or internet access
		- Easy -> Requires short range wireless
		- Moderate -> Requires limited physical access
		- Difficult -> Requires physical access to components

#### Equipment:
- Considers the type of equipment needed by the attacker to carry out the attack path
- Select the maximum level of equipment considering all steps of the attack
- Examples of equipment at each level:
	- Standard -> PC, oscilloscope, basic software radio
	- Specialised -> High end oscilloscope, manufacturer tools
	- Bespoke -> Focused ion beam workstation, Custom cryptographic key cracking hardware

#### TOTAL SCORE:
![[Pasted image 20250309132813.png]]

#### Risk Value Determination:
- Risk value is determined for each threat scenario based on:
	- The impact of the resulting damage if an attack is successful
	- The attack feasability of a successful attack aggregated across all attack paths per threat scenario
![[Pasted image 20250309133333.png]]

#### Risk Value Determination Matrix:
![[Pasted image 20250309133510.png]]
