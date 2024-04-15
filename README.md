## php 8.2x with MongoDB and Mongo-Express
1. Install Docker Desktop for Windows (x64). https://docs.docker.com/desktop/install/windows-install/
2. Open `Command Prompt` as `Administrator` and type `wsl --update`.
3. Install VS Code, use default options, add context to path. https://code.visualstudio.com/
4. Open VS code & update as needed.
5. Unzip https://netspace.in/netspace.in/assets/phpWithMongoDB.zip to a a folder you want to be the workspace.
6. Open the extracted folder, and right click `phpWithMongoDB` folder and select `Run with (VS) Code`.
7. On left pane, click `docker-compose.yaml`. 
8. **For first time installs of Visual Studio Code Only**, it may ask you in the bottom right corner of Visual Studio code to get `Docker` and `WSL` extension for VS Code- click yes. If this is needed, close VS Code after it's done installing, and repeat Step 6 and 7 after.
9. In VS Code, on the top menu bar, open a `Terminal > New Terminal`.
10. In VS Code terminal, Clear docker cache by running:
```
docker system prune -f
docker image prune -a -f
docker volume prune -f
```
- Note: This step is only neccessary because this example I built is of an interactive docker build and not a stored image.
11. Inside the VS Code Terminal, issue the start command `docker compose up -d`.
12. Click yes to firewall stuff as any pops up, you have a server now.
13. http://localhost:8000/ is your website.
14. http://localhost:8081/ is your database - admin/pass  is the HTTP basic auth. admin/password is the `MongoDB` password.
15. In the extracted folder you'll see it added files to the workspace, dont delete those, its the database. 
16. Change desired PHP in the `/app` folder.

Notes:
| function | how-to |
| --- | --- |
| **Stop** your server | Open your project folder in VSCode, then in the terminal type: `docker compose down`. |
| **Start** your server | Open your project folder in VSCode, then in the terminal type: `docker compose up -d`. (Omit -d to see all logs in terminal, ctrl-c stops) | 

#### **Run queries directly** from your server
Open your project folder in VSCode, then in the terminal type: 
```
docker exec -it mongodb bash
mongosh mongodb://admin:password@mongodb:27017
``` 
First command goes inside your docker container of `MongoDB`, the second one, from within that container, goes inside mongo itself.
