# Znuny-Telegram-Notification
- Znuny-Ticket-Notification-To-Telegram-Users Via Webservices
- Required at least Znuny 6.1.x

- This is only for Notification Owner Update.
- For others kind of notification, kindly create another Invoker. You may refer existing invoker (OwnerUpdate) and existing HTTP::REST Configuration.


1. A telegram bot must be created by chat with @FatherBot and obtain the token via Telegram.  


2. Import the 'Telegram Notification.yml' via Admin > Web Services


3. Update the telegram bot token at the created webservice.

	a) OTRS as requester > Network transport (HTTP::REST) > Configure
	
	b) Endpoint : https://api.telegram.org/botUPDATE_TELEGRAM_TOKEN_HERE
	
		e.g: https://api.telegram.org/botABCDEGH823742734984HJDFHhsdjghjjd

	c) Save and finish

	
4. Import and deploy ZZZAgentTelegram.xml at /opt/otrs/Kernel/Config/Files/XML/


5. Obtain the telegram chat_id for the agents:

		- update it into Agent Preferences > Miscellaneous > 'Telegram Chat ID' field. 
		- An agent must start the conversation with the created telegram bot (no 1) first by using telegram.  
		- By using  https://api.telegram.org/bot<TOKEN>/getUpdates , we can obtain the chat_id of the agent. 


6. Create a new Ticket Notification  

		- Event: NotificationOwnerUpdate
		- Select Recipients: (Should be owners)
		- Select Notification Methods: Webservices 
			-- Web service name: Telegram Notification
			-- Invoker: OwnerUpdate 
		
		- Notification Body and Text
			-- Anything as the actual value is set from XSLT itself.

[![s3.png](https://i.postimg.cc/mZ6vnwxN/Screenshot-2022-09-25-052244.png)](https://postimg.cc/F13Cd0H7)

