# Application Architecture



## General Thinking (without organization)

### Docker with webex chat bot app

bot that gets the time that the ISS passes over a city

Workflow:

- bot is inside a Webex roomu
- user sends bot a specific message
- webhook fires to warn bot
- bot gets the message with location to use
- bot searches mapquest to get the location GPS coordinates
- bot uses GPS coordinates to ask ISS Pass Time API to get info
- bot sends message back with city, date and duration of the ISS passing

### Hosting

Docker will be hosted in cloud provider

### Git

Necessary Git repositories:

- Webex application development (app-webex_iss_chat_bot)
  - Has all of the application code
  - Has the application tests
  - Has the supplementary code necessary to test the application
- Application Container (docker-webex_iss_chat_bot)
  - Has the information to build a Dockerfile for the application
- Application Infrastructure (iac-webex_iss_chat_bot)
  - Has the IaC for deploying and hosting the application
- Jenkins Infrastructure (jenkins-webex_iss_chat_bot)
  - Has the IaC for deploying and configuring the Jenkins server
  - Has the testing information for the application



Branches per repository:

- **app-webex_iss_chat_bot**
  - Development
    - Development of the application
  - Testing
    - Unit testing 
  - QA
    - Integration testing using the docker image
  - Staging
    - Integration testing using an environment equal to production
  - Production
    - Production code
- **docker-webex_iss_chat_bot**
  - Development
    - Development of the Dockerfile and container
  - QA
    - Integration testing using the docker image
  - Staging
    - Integration testing using an environment equal to production
  - Production
    - Production code
- **iac-webex_iss_chat_bot**
  - Development
    - Development of the infrastructure
  - Staging
    - Integration testing using an environment equal to production
  - Production
    - Production code
- **jenkins-webex_iss_chat_bot**
  - Development
    - Development of the infrastructure
  - QA
    - Integration testing using the docker image
  - Staging
    - Integration testing using an environment equal to production
  - Production
    - Production code



Tasks to be performed in each branch:
	Development
		Where the code for the application, dockerfile and any further files will reside
	QA
		when a PR is made from Dev to QA and is accepted the following tasks should be performed:
			- The Docker container should be built using the Dockerfile and application;
			- The container needs to run;
			- Something should create a test Webex room for QA testing;
			- Something should send a message to this room;
			- Something should get the last message in the room;
			- Something should send this message to the container to simmulate the Webex Webhook;
			- The container should 