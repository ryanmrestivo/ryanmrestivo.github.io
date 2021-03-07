# CISSP-Tips
My collection of valuable knowledge to assist in teaching and mentoring others towards the CISSP exam.

## Risk Management

SLE = AV * EF
 - Single Loss Expectancy (SLE) - Negative impact for one-time occurrence
 - Asset Value (AV)
 - Exposure Factor (EF) - If a flood will damage 40% of your data center, EF is 40%

ARO
 - Annual Rate of Occurance

ALE = ARO * SLE
 - Annual Loss Expectancy = Rate of Occurrence - Single Loss Expectancy

## Threat Modeling

STRIDE - Microsoft threat modeling tool
- **S** poofing
- **T** ampering
- **R** epudiation - attacker can deny participation
- **I** nformation disclosure
- **D** enial of service
- **E** levation of privilege

## Control Types
PTA keeps the children safe!
* **P** hysical - Tangible. Locks, guards, alligator moats, etc.
* **T** echincal/Logical - Automated or electronic systems.
* **A** dministrative - Policy, signage.

## Due Care vs Due Diligence
Imagine you have a pool. To protect children and animals from drowning in your pool, you exercise due care by building a fence around the pool. Regularly checking the fence for vulnerabilities and correcting them demonstrates due diligence.

* Due Care - A vendor engaging in a reasonable and expected manner for the circumstance
* Due Diligence - Demonstrates due care

## Security Models

### Brewer-Nash
Brewer-Nash is also known as "The Chinese Wall" and protects against conflict of interest. Remember Chinese "brew" tea. :tea:

### Simple Security vs \*-Security

You must read before you can write. So reading is "simpler" than writing. This makes reading the simple security model and writing the \*-security model.

### Integrity vs Confidentiality models
* Integrity Models have the letter "I" in them.
* Bell LaPadula and Biba -  Since Biba has an "I" I it, it is integrity. The two are opposite so Bell is confidentiality. For some something confidential you don't want a subject reading up above their security. So Bell has a no read up property. With this we can extract read and write for both Biba and Bell

|Bell       |Biba           |
|-----------|---------------|
|No Read Up |Read Up        |
|Write Down |No Write Down  |

## Factorization of Primes vs Discreet Logs
Found this somewhere else but it made me laugh and was easy to remember:
Mr. Diffie-Hellman and Dr. ElGamal are phantom poopers! They leave discreet logs!

## DES Modes of Operation
Most important thing here is remember strength from weakest to strongest. No clear mnemonic to do this. My approach:
* Remember the first and the last.
* The center 3 are alphabetical by name and/or abbreviation.

1. ECB - Electronic Code Block (also the only one that doesn't support an initialization vector)
2. CBC - Cipher Block Chaining
3. CFB - Cipher Feedback
4. OFB - Output Feedback Mode
5. CTR - Counter

## Cloud Computing Operating Model
IaaS, PaaS, SaaS - [Remember Pizza as a Service](https://medium.com/@pkerrison/pizza-as-a-service-2-0-5085cd4c365e)


## Fire Classes and Extinguisher Types

|Type |Mneumonic    |Description                  |
|-----|-------------|-----------------------------|
|A    |Ash          |Ordinary solid combustibles  |
|B    |Boil, Bubble |Flammable liquids and gasses |
|C    |Circuits     |Electrical equipment         |
|D    |Dent         |Combustible metals           |
|K    |Kitchen      |Oils and fats                |

## Ring computing model

Remember "Zero KODU"

|Layer  |Purpose              |
|---    |---                  |
|0   	  |**K**ernal           |
|1   	  |**O**perating System |
|2   	  |**D**rivers          |
|3   	  |**U**ser             |

CMMI (I Really Defend My Opinion)
1. Initial
2. Repeatable
3. Defined
4. Managed
5. Optimized

SLE = AV * EF
Single Loss Expectancy (SLE) - Negative impact for one-time occurrence
Asset Value (AV)
Exposure Factor (EF) - If a flood will damage 40% of your data center, EF is 40%
ARO

Annual Rate of Occurance
ALE = ARO * SLE

Annual Loss Expectancy = Rate of Occurrence - Single Loss Expectancy

Threat Modeling
STRIDE - Microsoft threat modeling tool

S poofing
T ampering
R epudiation - attacker can deny participation
I nformation disclosure
D enial of service
E levation of privilege

Control Types
PTA keeps the people safe!

P hysical - Tangible. Locks, guards, alligator moats, etc.
T echincal/Logical - Automated or electronic systems.
A dministrative - Policy, signage.

Due Care vs Due Diligence
Imagine you have a pool. To protect children and animals from drowning in your pool, you exercise due care by building a fence around the pool. Regularly checking the fence for vulnerabilities and correcting them demonstrates due diligence.

Due Care - A vendor engaging in a reasonable and expected manner for the circumstance

Due Diligence - Demonstrates due care

##### Asymmetric Encryption  
> Also known as public key encryption (public key can be publicized without compromising security)<br>
  Remember: <ins>DEREK</ins>   
  * <ins>D</ins>iffie-Hellman/<ins>D</ins>SA 
  * <ins>E</ins>l-Gamal 
  * <ins>R</ins>SA
  * <ins>E</ins>lleptical Curve Cryptography (ECC)
  * <ins>K</ins>napsack
--------------------------------------------------------------------------------------------------------------------------
##### Symmetric Encryption  
> Also known as [s]hared key or [s]ecret key encryption.  Private key can be sent out-of-band<br>
  Remember: <ins>23BRAIDS</ins>   
  * <ins>2</ins>TwoFish
  * <ins>3</ins>DES
  * <ins>B</ins>lowfish
  * <ins>R</ins>C5
  * <ins>A</ins>ES
  * <ins>I</ins>DEA
  * <ins>D</ins>ES
  * <ins>S</ins>AFER/Skipjack
--------------------------------------------------------------------------------------------------------------------------
##### Hash Functions: 
> Think of the good doctor: <ins>SHA HAVAL, MD</ins>
* MD can create a 128-bit hash value.  SHA can create a 160-bit hash value (SHA-1), SHA-256 produces a 256-bit hash , SHA-384 produces a 384-bit hash, and SHA-512 produces a 512-bit hash.
--------------------------------------------------------------------------------------------------------------------------  
##### OSI Model:  
> Physical (Level 1), Datalink, Network, Transport, Session, Presentation, Application (Level 7)<br>
  Remember: 
  * "Please Do Not Throw Sausage Pizza Away" (going up)
  * "All People Seem To Need Data Processing" (going down)
--------------------------------------------------------------------------------------------------------------------------
##### Risk Management
  * ALE = ARO x SLE   *think  "Ale causes arousle" 
  * SLE = AV x EF     *think Italian magician (or Mario) saying "I've got something up my sleav-ef"
  
--------------------------------------------------------------------------------------------------------------------------  
##### 4 D's of Physical Security: 

> [D]eter → [D]eny → [D]etect → [D]elay

--------------------------------------------------------------------------------------------------------------------------
##### Multi-Factor Authentiation:  

> Something you <ins>know</ins>, something you <ins>have</ins>, something you <ins>are</ins>

--------------------------------------------------------------------------------------------------------------------------
##### TCP Header Flags:  

> **URG  ACK  PSH  RST  SYN  FIN**

*think "<ins>U</ins>nskilled <ins>A</ins>ttackers <ins>P</ins>ester <ins>R</ins>eal <ins>S</ins>ecurity <ins>F</ins>olks"
  
--------------------------------------------------------------------------------------------------------------------------
##### Confidentiality and Integrity Models
* <ins>Simple</ins> Property: for read "Reading is simpler than writing."
* <ins>Star</ins> Property:  for write  "It's written in the stars."

Biba and Clark Wilson have the letter **i** in them, so Integrity Models
Bell-LaPadula is confidential:  No read up and No write down.  (said another way, **Bell is WURD**) 
  * Remember:  You don't want someone read up above their security level
  
Biba will be opposite:  No read down and no write up  (**Biba is NO WURD**) 
  * Remember: you can't write up as it would "pollute" the data
--------------------------------------------------------------------------------------------------------------------------             
##### System Security Modes 

>that is, for systems that process classified data, what each user is required to have

  * <ins>Dedicated mode</ins> - have a security clearance, access approval, and valid need to know for **ALL** data processed by Dedicated system 
  
  * <ins>System High mode</ins> - have a security clearance and access approval for **ALL** data processed by System high mode system.  Also, valid need to know for data **PERSONALLY** accessed.
  
  * <ins>Compartmented mode</ins> - have a security clearance for **ALL** data processed by compartmented mode system.  Also, access approval and a valid need to know for data **PERSONALLY** accessed.
  
  * <ins>Multilevel mode</ins> - have a security clearance, access approval, and valid need to know for data **PERSONALLY** accessed.  (Requirements are enforced primarily by hardware or software on the system, not by limiting physical access)

--------------------------------------------------------------------------------------------------------------------------
##### Network Topologies
* <ins>ring</ins> topology is most **secure**. (if it is dedicated with no external connections)
* <ins>bus</ins> topology is cheap, easy to set up, and good for small LANs. (If the single line of cable breaks, the network is down, devices can see others' packets)
* <ins>star</ins> topology is most **common**.  (more resilient than two above if a device fails, but still dependent on central switch or hub)
* <ins>mesh</ins> topology is best for **redundancy**.  (with **Full mesh** if a node fails, network traffic can be directed to any of the other nodes) 
              
Note: There is also **partial mesh**, some nodes are organized in a full-mesh scheme, but others are connected to only one or two in the network. Partial mesh topology is commonly found in peripheral networks connected to a full meshed backbone network.)
   

--------------------------------------------------------------------------------------------------------------------------
##### DR Recovery Sites 

* <ins>Hot site</ins>- Organization needs site activation **immediately**; ready to go within **minutes or hours**.

* <ins>Warm site</ins>- Organization has alt. site with equipment and data circuits available but nothing is connected and everything needs to be set up.  The main requirement in bringing a warm site to full operational status is the transportation of appropriate backup media to the site and restoration of critical data on the standby servers.  This can take from a a **one to three days.**  (Sybex says as little as 12 hrs., other sources 24-48 hrs.)

* <ins>Cold site</ins>- Organization has alternate site with power and cooling, but equipment needs to be ordered and may take a **few days to several weeks** to arrive, be configured, and then restoration of backup media.
          
--------------------------------------------------------------------------------------------------------------------------
##### Inherited and Explicit Rights and Permissions

* <ins>Rights</ins>- grant users ability to perform specific actions on a **system**.
* <ins>Permissions</ins>- enable users to read, write to, or execute **files**, that is a particular object on a file system.
* <ins>Inherited</ins>- user account inherits as a result of being a member of a security **group** that has been assigned that right.
* <ins>Explicit</ins>- assigned to a user at the **user account** level.
          
--------------------------------------------------------------------------------------------------------------------------
##### Change Management, Configuration Management, Incident Response, BCP, and Electronic Discovery Steps
> Change Management Steps:
  * 1. Request the change
  * 2. Review the change
  * 3. Approve or reject the change
  * 4. Test the change
  * 5. Schedule and implement the change
  * 6. Document the change

> Configuration Management Steps:
  * 1. Baselining
  * 2. Patch management
  * 3. Vulnerability management
  
> Incident Response Steps:  
  * 1. Detection
  * 2. Response
  * 3. Mitigation
  * 4. Reporting
  * 5. Recovery
  * 6. Remediation
  * 7. Lessons Learned
          
> BCP Steps:  
  * 1. Develop a BCP policy statement
  * 2. Conduct a BIA
  * 3. Identify preventative controls
  * 4. Develop recovery strategies
  * 5. Develop an IT contingency plan (DRP)
  * 6. Perform DRP training and testing
  * 7. Perform BCP/DRP maintenance
  
> Electronic Discovery Steps:  
  * 1. Identification: potentially responsive documents are identified for further analysis and review
  * 2. Preservation: data identified as potentially relevant is placed in a legal hold to ensure it cannot be destroyed
  * 3. Collection:  transfer of data from a company to their legal counsel
  * 4. Processing: Various data culling techniques are employed during this phase, such as deduplication and de-NISTing
  * 5. Review: documents are reviewed for responsiveness to discovery requests and for privilege
  * 6. Production: documents are turned over to opposing counsel, based on agreed-upon specifications
 
--------------------------------------------------------------------------------------------------------------------------
##### MISCELLANEOUS

* Retinal scan is most intrusive to privacy.

* Life is more important than any other consideration.

**Entrapment** is when law enforcement persuades someone to commit a crime that they otherwise would not have committed. 
**Enticement** is when the person would have committed (or intended to commit the crime) anyway.   (Source: Sybex OSG 7th Ed.)
  (Think: You can entice a criminal, but only entrap an otherwise honest person.)
          
* False Positive (Accept) - ACS identifies unauthorized user as authorized user
* False Negative (Reject) - ACS does not validate an authorized user (Note: more acceptable than false accepts)

**Pipelining** - method by which CPU can process more than 1 instruction per clock cycle
> Fetch -> Decode -> Execute -> Write
Once an instruction moves on to next stage, a new instruction can be fetched

**need to know** - user has no access to info. that is not required by the user
Example:  Restricting a CIO from accessing financial reports

**least privilege**- user has no more access to a resource than what is required to do that user's job
Example: User who reviews sales figures has read-only access, but cannot modify them
