### The Theory and Math Behind Data Privacy and Security Assurance

#### Takeways
* Need to automate access controls for access organizations
* How AWS is scaling provable security

#### Zelkova
* Audit
* Checks
* Identifies
* Detects

#### What does math and logic buy me?
* Reason about access control instead of regex
* Algorithms not policies to prove IAM roles...

#### Satisfiable
* NP-complete problem - no jnown algorithm to efficiently determine satisfiability (not x and x)
* x^2 - 4 = 0 is satisfiable
* SMT solvers - microprocessor verficiation, aerospace applications

#### Encode IAM Policies as Logical Formulas
* Allow and deny statements
* 10^12 aws accounts * 5000 actions * 10^13 resources * infinite condition key values - cannot fuzz or test
* Zelkova creates boundaries without enumerating

#### How to encode policies as logical formulas
* Use SMT solvers to determine policy is compliant with governance rule

#### Workflow
* Config -> Amazon SNS -> Lambda -> zelkova Lambda-> IAM, S3, IoT device conatainer

#### Bridgewater Example
* Zelkova is first formal and methodical way to analyze AWS policies
* Can ask specific principles about policies
* Can make hypothetical policies and test them out
* Workloads span a fleet of AWS accounts
* Eliminate vulnerabilities in cloud configuration that threaten data security, access controls, and compliance
* Detect misconfigurations, check planned changes for defects, identify policies that need to change, audit policies
* Process - on each policy change
    * Monitor and collect policy JSON for all AWS accounts
    * Call Zelkova for properties and comparisons against threat modeling constraints
    * Detect trouble before it hurts us

#### Takeaways
* Provable security wfor the win (in code)