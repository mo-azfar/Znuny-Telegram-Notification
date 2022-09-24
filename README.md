# Znuny-Telegram-Notification
- Znuny-Ticket-Notification-To-Telegram-Users Via Webservices
- Required at least Znuny 6.1.x

1. A telegram bot must be created by chat with @FatherBot and obtain the token via Telegram.  


2. Import the 'Telegram Notification.yml' via Admin > Web Services


3. Update the telegram bot token at the created webservice.

	a) OTRS as requester > Network transport (HTTP::REST) > Configure
	
	b) Endpoint : https://api.telegram.org/botUPDATE_TELEGRAM_TOKEN_HERE
	
		e.g: https://api.telegram.org/botABCDEGH823742734984HJDFHhsdjghjjd

	c) Save and finish

	
4. At Invoker (Webhook), check mapping for outgoing data (XSLT)
	
	a) <text><xsl:value-of select="//NotificationPlainBody" /></text> = The text value will be taken from configured Ticket Notification or you can define your text here
	
	*Only text are acceptable here.

	
5. Import and deploy ZZZAgentTelegram.xml at /opt/otrs/Kernel/Config/Files/XML/


6. Obtain the telegram chat_id for the :

		- agents and update it into Agent Preferences > Miscellaneous > 'Telegram Chat ID' field. 
		- An agent must start the conversation with the created telegram bot (no 1) first by using telegram.  
		- By using  https://api.telegram.org/bot<TOKEN>/getUpdates , we can obtain the chat_id of the agent. 


7. Create a new Ticket Notification  

		- Event: Up to you
		- Select Recipients. (Should be agents only whos has telegram chat id updated into their profile (no 6 above) ).
		- Select Notification Methods: Webservices 
			-- Web service name: Telegram Notification
			-- Invoker: Webhook 
		
		- Notification Text
			-- keep it simple. 1 line only!!!

[![s4.png](https://i.postimg.cc/CLB3pqSy/Screenshot-2022-09-25-052348.png)](https://postimg.cc/dLFH8Dhn)
[![s3.png](https://i.postimg.cc/mZ6vnwxN/Screenshot-2022-09-25-052244.png)](https://postimg.cc/F13Cd0H7)

