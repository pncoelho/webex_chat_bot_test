Docker with webex chat bot app
	bot that gets the time that the ISS passes over a city
		bot is inside a room
		user sends bot a specific message
		webhook fires to warn bot
		bot gets the message with location to use
		bot searches mapquest to get the location GPS coordinates
		bot uses GPS coordinates to ask ISS Pass Time API to get info
		bot sends message back with city, date and duration of the ISS passing


Docker will be hosted in cloud provider


Git Repo should be devided in 4 branches:
	- Development
	- Unit testing
	- QA
	- Staging
	- Production

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