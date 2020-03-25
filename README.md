[![Gitter](https://badges.gitter.im/TrustSource/community.svg)](https://gitter.im/TrustSource/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

# ts-core - the heart of TrustSource
Core of TrustSource, managing most of the service functionality, especially flow logic. See https://support.trustsource.io for more details.

## About
TrustSource is an open source solution for implementing an [OpenChain](https://www.openchianproject.org) compliant open source compliance process. It currently is availabe as source code (this repo) for an on-premises setup as self managed installation or as [managed service](https://app.trustsource.io). In a few weeks we also will provide a hosted version as an AWS marketplace offering. Learn more about the different options [here](https://www.trustsource.io/editions). It is also possible to obtain a support contract or [request consulting](https://www.eacg.de/contact).

Trainings and further materials can be found at the publicly accessible [TrustSource Knowledgebase](https://support.trustsource.io). 

To become part of the TrustSource eco-system feel free to reach out to the TrustSource Team at ecosys @ trustsource.io.

## Getting started
For over 10 years meanwhile we are involved with the topic of opne source compliance. Since then a lot has changed and we learned a lot. However, the complexity remains high. To simplfy the entry, we have provided some materials to support your compliance endeavour. We would suggest the following sequence:
  1. [Learn about OS compliance](https://www.slideshare.net/JanThielscher/open-source-governance-erfahrungen) - (a presentation held by [Jan](https://www.linkedin.com/in/jthielscher/) to the opensource workgroup of the Bitkom 2018)
  2. Setup TrustSource (next topic)
  3. Integrate TrustSource with your [CI/CD chain](https://support.trustsource.io/integrations) 


## Setup of TrustSource
As TrustSource is not just a tool you download and start querying through its CLI, it requires a bit of preparation and planning. TrustSource comprises of several services following partly the functional seggregation defined by the [OC-Tooling Working Group Capabilities Map](https://github.com/Open-Source-Compliance/Sharing-creates-value/tree/master/Tooling-Landscape). 
The following diagram gives an overview of the maximal installation:
(deployment_max_img)
The core (this) component will provide the UI, user management, roles, logging, basic API, flow-logic, most business logic, black & white lists, all governance and reporting features. It requires a Mongo-DB to start up.

### 1. Provide a mongo DB-Service 
```
$ docker pull mongo
...
$ docker run --name some-mongo -d mongo:latest
```
Where ```some-mongo```shall be the name you want your mongo image to operate. 

### 2. Provide TS-Core-Service
PLEASE NOTE: In our operational environments we make use of AWS services like KMS and Secrets Manager. However, for our developers we have a switch to allow providing local configurations

You may choose to build it from this repository or use an image from docker hub:
```
$ docker pull ts-core
...
$ docker run --name ts-core -d -e ts-core:latest
```
You may consider putting all images into a separate network. However, if you plan to provide the services across your organization you will need an endpoint that you will publish. Make sure, the services will be able to reach each other.

Todo:
  Access port?
  first user? Link to role management

Now you may login to TrustSource app and start using the core services. But yet there is not much content available. To change this, additional services need to be set up:

### 3. Launching component crawlers
See [ts-crawlers](https://github.com/trustsource/ts-crawlers) repository for details.

### 4. Launching vulnerability crawler
See [ts-vulncrawler](https://github.com/trustsource/ts-vulncrawler) repository for details.

### 5. Providing TS-LegalCheck-Service
See [ts-legalcheck](https://github.com/trustsource/ts-legalcheck) repository for more information.

### 6. Provide TS-SPDX-Im&Export-Service (optional)
See [ts-spdx](https://github.com/trustsource/ts-spdx) repository for more details.

### 7. Integrate with your CI/CD chain
Depending on your programming language you will require different toolsets. [This article](https://support.trustsource.io/hc/en-us/articles/115003456825-Which-integrations-are-available-for-TrustSource-) gives an overview how integrations may be achieved and links to the different repositories.  

## Future directions
To learn more about the future directions, please see our [Roadmap](https://support.trustsource.io/hc/en-us/articles/360011448239-Roadmap)
Feel free to use this repository to suggest features, improvements or bugs. Every "issue" is welcome. Please use tags accodingly to help indentify what it is about.

## Contribute & Communicate
We highly encourage all sorts of communication. We are here to help your compliance efforts taking up. For sure we also need to make our living, thus support contracts are welcome. But we also want to give back to the community that has offered so much to allow our work. If you want to reach out to us, please use one of the following channels:
    * our [FAQ](https://support.trustsource.io/hc/en-us/sections/115000775369-TrustSource-FAQ)
    * the [Knowledgbase](https://support.trustsource.io)
    * [Issues](https://github.com/trustsource/ts-core/issues) - please use the correct repository!   
    * [Support subscriptions](https://www.trustsource.io/support)
    * [DevChannel](https://gitter.im/TrustSource/community) 4 contributors (via gitter) 
    
In case you plan to contribute, you are highly welcome! We maintain a taskboard on Jira, which is linked to the issues of the correpsonding repos. Thus it is reltively simple to join work. However, some setup for the different developments might be required. Shortly we will provide a description on how to setup a dev env for each of the different environments. Meanwhile feel free to fork the repo and start working. We will be happy to receive your pull request. The pull request should provide the typical information such as 
    * What has changed?
    * Why?
    * How has it been tested?
    
PLEASE NOTE: Whenever you will be contributing something, you will have to state that you will comply with the contribution agreement. This means you will hand an non-exclusive, irrevocable, unlimited right to use, modify and distribute your contribution to the TrustSource project. For further details, please see the [contribution agreement](https://github.com/trustsource/CONTRIBUTION) in this repository.

