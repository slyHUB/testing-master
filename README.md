testing
=======

Test App to test Git Hub



Flux
Basics
This proposal is in the Project Proposal Phase (as defined in the Eclipse Development Process) and is written to declare its intent and scope. We solicit additional participation and input from the community. Please add your feedback in the comments section.
Parent Project: 
Technology Project
Background: 
The development tooling landscape is changing and moving towards cloud-based developer tooling. While this movement is what everybody is talking about, a clear vision of how cloud-based developer tooling will look is still missing. Converting the existing desktop-based IDEs into something that runs in the browser seems to be the wrong approach.
At the same time all of the cloud-based approaches seem to be fully disconnected from the existing desktop-based IDEs. They require that developers “move over” into the cloud for doing their development. Often they have to leave existing tools behind while the new cloud-based tooling is missing important functionality that people use every day in their existing desktop IDEs. There is a need to bridge this gap.
Scope: 
This project aims at designing and implementing a new architecture and infrastructure for integrating development tools across desktop, browser, and servers. The goal is to provide an extremely flexible platform and infrastructure that allows new cloud-based tooling components to be built highly decoupled from each other and that bridges the gap to existing desktop IDEs at the same time.
Therefore the project aims at implementing this base infrastructure and will provide connectors to the most widely used desktop developer tools (like Eclipse, IntelliJ, Netbeans, or plain text editors). In addition to that the cloud-based tooling for a limited set of languages on top of this infrastructure will be built to demonstrate how language tooling could be implemented for this cloud-based tooling architecture. We will start with Java and JavaScript tooling that works on this cloud-based infrastructure and that is implemented by re-using parts of JDT and Orion for implementing cloud services. Maybe additional services for other languages will follow.
Out of Scope
The project doesn’t aim at re-implementing a full-featured desktop IDE in the browser and doesn’t plan to re-implement most of the existing language tooling that is out there in the Eclipse universe. Instead the goal will be to re-use the capabilities of existing tools by making those capabilities available as cloud based services.
Description: 
The fundamental architecture of the project consists out of three building blocks:
the backbone is a distributed messaging architecture that doesn’t know anything about language tooling, but that is able to distribute messages in a highly distributed environment in real-time at low latency. This messaging works between server processes, between processes running in different cloud environments, and between client applications like browser-based front-ends.
the fundamental concept on top of this distributed messaging architecture is the notion of repositories that can contain projects, resources, and metadata. By using the messaging system, repositories can keep projects/resources locally and sync projects/resources with other repositories running somewhere else.
in addition to repositories and messages, services can connect to the messaging system, can sync data to their local storage mechanism (files, database, whatever), work on that data, and provide additional resources or metadata for the projects/resources.
As a first step, existing desktop IDEs can act as repositories. This allows additional cloud-based services and/or front-ends to be implemented that work on those projects/resources (like editing your project files using a browser-based editor).
As a second step, additional cloud-based services can provide additional features for those projects/resources, ranging from doing “compilation as a service” for error reporting, static analysis, providing smart content-assist, navigation, etc.
This allows developers to connect their existing, still locally stored projects/resources to be connected to the cloud and working on those projects/resources in the cloud at the same time. There is no need to “completely move over” with everything into the cloud. People can choose what and when to use cloud-based tooling while they continue to use their favorite local tools at the same time.
In addition to that the cloud-based services can be implemented in a language and environment of their choice. While a compilation/navigation/refactoring service for Java might re-use the existing Eclipse JDT implementation in a headless way, the same service for JavaScript might want to run on top of a Node.js runtime and re-use libraries such as Tern or ESLint.
Relationship to Orion
The Eclipse Orion project also aims to provide cloud-based tooling infrastructure but the architectural focus is quite different. The main focus of Orion so far has been on browser-based integration and tools that run client-side in the browser. Flux provides a server-focused tooling service architecture that enables both integration between tooling servers, between server and browser client, and between servers and traditional desktop clients. We view these architectures as strongly complementary. Browser-based integration is highly scalable, and enables a more strongly integrated user experience across multiple browser-based tools. Server-side integration enables connection of deeper, long running tools, and legacy tools. Flux will integrate with Orion’s browser-side integration technology where possible, and reuse JavaScript tooling developed in the Orion project. In the long term combining these technologies under a common top-level project may be appropriate.
Why Here?: 
The underlying architecture is fully independent of any existing desktop IDE (including Eclipse) and all of them could and should be connected to this new infrastructure from the beginning. Nevertheless the power of this approach is that it allows many companies and people to collaboratively implement cloud-based developer tooling - by working on independent services providing a wide variety of features for different languages, execution environments, and more.
At the same time the project opens the door for many existing Eclipse-based developer tools and people/companies who are working on them to re-use existing bits and pieces of their projects in a next-generation cloud-based development environment.
Licenses: 
Eclipse Distribution License 1.0 (BSD)
Eclipse Public License 1.0
Legal Issues: 
This project will be distributed under both the Eclipse Distribution License and the Eclipse Public License. We believe a BSD-style license is required for broad adoption of the project technology in the web community.
The project source code will be hosted at GitHub (and mirrored back to git.eclipse.org).
Project Scheduling: 
We are aiming to produce an initial incubating release to coincide with the June 2014 Luna release train, but the planning is still very vague at the moment. So this plan might change.
Future Work: 
The work areas will be:
basic messaging infrastructure (highly scalable cloud-based and distributed messaging system, including authentication and basic security features, capable of syncing resources and of real-time sync while typing)
Java language tooling (cloud-based services and browser-based editor extensions that make Java development a pleasure in this environment).
JavaScript language tooling (cloud-based services and browser-based editor extensions that make JavaScript development a pleasure and goes beyond existing JavaScript tooling)
cloud-based application deployment and execution services (deploy apps on PaaS environments like Cloud Foundry and others, execute applications without explicit deployment for quick turnaround cycles, possibly includes debugging integration)

HidePeople
Project Leads: 
Martin Lippert
John Arthorne
Committers: 
Andy Clement
Kris De Volder
Nieraj Singh
Alex Boyko
Ken Walker
Mike Wilson
Simon Kaegi
Curtis Windatt
Anthony Hunter
Martin Lippert
John Arthorne
Mentors: 
John Arthorne
Maximilian Koegel
Interested Parties: 
Pivotal
IBM
RedHat
Rapicorp
Markus Knauer
itemis

HideSource Code
Initial Contribution: 
The initial contribution has been donated by Pivotal. The current code base has been developed by a few developers over a few months. All code in the initial contribution is authored by Pivotal employees and the copyright is held by Pivotal.
The initial contribution has the following third party dependencies:
Socket.IO
Socket.IO-client
org.json
express.js
...
The initial code contribution is prototype and proof-of-concept work only and by no means a complete nor stable implementation of the described architecture and cloud services.
Source Repository Type: 
GitHub
Source Repositories: 
https://github.com/spring-projects/flight627
