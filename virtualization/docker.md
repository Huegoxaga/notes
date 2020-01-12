Docker
Download image	docker pull folder/software_name
Run software 		docker run -d --name sql_server_demo -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=reallyStrongPwd123' -p 1433:1433 microsoft/mssql-server-linux

Here’s an explanation of the parameters:

-d
This optional parameter launches the Docker container in daemon mode. This means that it runs in the background and doesn’t need its own Terminal window open. You can omit this parameter to have the container run in its own Terminal window.
--name sql_server_demo
Another optional parameter. This parameter allows you to name the container. This can be handy when stopping and starting your container from the Terminal.
-e 'ACCEPT_EULA=Y'
The Y shows that you agree with the EULA (End User Licence Agreement). This is required in order to have SQL Server for Linux run on your Mac.
-e 'SA_PASSWORD=reallyStrongPwd123'
Required parameter that sets the sa database password.
-p 1433:1433
This maps the local port 1433 to port 1433 on the container. This is the default TCP port that SQL Server uses to listen for connections.
microsoft/mssql-server-linux
This tells Docker which image to use.

Check the Docker container 	docker ps


Start a stopped container   	docker start sql_server_demo
