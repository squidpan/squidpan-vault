---
categories:
  - "[[People]]"
tags:
  - people
birthday: 1963-07-03
org: []
created: 2025-10-17
---
## Preamble

NPQS provides consolidated streaming prices to markets data consumers both on prem and in the cloud. My primary responsibility within the squad is to ensure every __Prime release is successfully deployed__ to integration environment first followed by all higher environments (QA, PROD).

Requirements from Business, Infrastructure and bank wide strategic initiatives (e.g. tech depths/future proofing/cloud migration) drive the releases of NPQS and deployment cycle (1-2 months). I work with the product owner and scrum master to define the body of work at the initial planning stage and create JIRA tickets for development team members if needed.

I work on documenting key NPQS functionality when communicating with businesses and other stakeholders
documenting, testing, deploying on NPQS releases to all Linux environments. I also worked with the product owner and scrum master to create JIRA tickets for team members.

## Experience

### Documentation - NPQS

- NPQS Data (Ticker, Benchmark) distribution to Internal Consumer applications (connection, distribution type (files, views))
- NPQS release deployment steps documents
- NPQS failover/switchover documents
- NPQS Data (C0 data distribution fields)
- NPQS Gateways (5) 
- Price Leader mechanism
- Suspect processing/Workflow
- MBS Payup tools - new feeds IMG, TSAR
- Architecture diagrams and PPTX

### Requirements and JIRA

- Functional requirements from the Business through Product owner, Scrum master
- Non functional requirements from Infrastructure and Bank wide Strategic initiatives and architecture, BAU
- NPQS body of work created as JIRA epics and stories
- Each NPQS release is planned from a prioritized list of items that need to be delivered

### NPQS requirements releases and deployments - Prime classic in Linux

My primary responsibility within the squad is to ensure every Prime release is successfully deployed to all higher environments (QA, PROD).

Starting in our Pre-QA environment, I follow directions from Edward Chubin, our technical lead in all things deployment, Linux, coding, github (super important) and shows. I test out all deployment commands, revise documentation accordingly and perform basic testing (e.g. suspect data cleansing using workflow, data quality reports review, etc.) before we collectively bless the release worthy of a trip to higher environments.

As part of the release process, the new code is reviewed with the rest of the developers where questions are addressed and issues identified and resolved.

On the day of deployment, all technical staff (system engineer (se), dba and Operations Support team follow the steps I call out and execute the commands.

I helped setup Jira tickets for the squad when requested by the Product owner and scrum master. I have been learning cloud concepts in a timely manner.

### Workflow and regression test PRIME

#### Suspect Price cleansing aka workflow
is a process that takes 4 times a day right after each benchmark job run at (0840 1130 1415 1530)by the pricing team. Pricing team uses AC Admin desktop, a thick Java client locally installed (or VDI), whIch connects to the PRIME backend (ie INT_acint1) and provides an interface to cleanse suspect prices and enforces 4 eyes on cleanse/validate/accept-reject approval actions by preventing anyone member to approve his own changes. For each PRIME release, 4 eyes enforcement is tested via 2 users each logging in with the role of Guardian and Inspector roels respectively as DAS_S, DAS_S_2.

```code
Workflow suspect cleansing Testing steps
1. DAS_S(user with Guardian role) logs into AC Admin desktop as DAS_S
2. Module > Workflow
   Select Workflow suspect folder to cleans (e.g. BENCHMARK_0840, BEMCHMARK_1130, etc)
3. Click on suspect, right click to [Manually modify/ Just Validate, etc] and SAVE
4. Suspect item flows from Suspect Folder to Approval Folder
5. Login as DAS_S_2 and perform (Accept/reject) actions on the item in Apporval folder < right click find acceptable, Accept and Save > DAS_S will fail if attempting to Accept his own updates
```

#### Data quality consistency and regression tests
in INT environment, data quality is assessed by comparing 2 versions, the released (Tag69) to current PRIME Prod version (INT_acdba - Tag68) by looking at the QC reports. QC reports provides the extent of discrepancy between two consecutive releases. Realtime comparisons of a given security and at eh 'same' point in time requires visually inspecting the differences.





### OPS360 - Cloud distribution

I have been proactive in my learning of cloud computing concepts (Kubernetes, Rest API, etc) to have skills that are relevant to support the current NPQS pricing data distribution through Ops360 microservices in both the Private cloud (Openshift 4) and Government cloud (CFS2.0). The learning path is steep and long and I intend to chip away at it consistently.

Creating together in some capacity beyond the Prime arena is the goal. The current high priority effort, Spline application, is being built to improve upon the current solution that is complex and obscure in its implementation soon to be sunset - this is an opportunity for me to learn and sink my teeth into it in whatever capacity (i dont care what) and get my foot in the door. For that I will be working closely with Mr. Spline our resident SME/expert in ops360 cloud stuff.

dataviews/models, saved search need to be setup for new endpoints

### Current Focus and Interests
documentation: Spline API and others
testing: Rest API testing using Postman
CI/CD using Gitlab

- 
- 
- the Bank's markets pricing data hub for several key consumer applications
- NPQS squad that consists of Product Owner, Scrum master, developers, Ops, DBA, SA, Infrastructure, etc.
- managed JIRA tickets for the development team, creating tickets with initial description, initial estimates, pertinent background information
- Deployment steps documentation that followed on the day of deployment by SA, DBA and OPS
- Documentation
	- Confluence, VS code, Draw.io, Plantuml, Excel
- Interests
	- Rest API, swagger, Spring Boot Web MVC, React, node
	- K8s, microservices
	- gitlab, postman
	- grafana, Prometheus
	- helm
	- oauth2, Okta
	- java/maven
	- OCP4
	- Proxmox
	- Reading books, Writing, music, smoking

the market data pricing services from end to end. with worked closely I spend most of my working hours listening, taking notes, making drawings


## Meetings

![[Meetings.base#Person]]