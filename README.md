# drone-ci-example
Follows the Getting Started guide at https://docs.drone.io/server/provider/github/

# Authorizing the Drone Server with your GitHub
Multiple processes will need to stay running to make this work, and ideally they won't be interrupted or 

1. Install ngrok and tmux
2. Make a tmux session called `drone-ngrok` and run `ngrok http 80` in it. This will expose port 80 on your computer to the wider internet via a random URL of ngrok's choosing. The output of that function should look like
```
ngrok by @inconshreveable     (Ctrl+C to quit)

Session Status                online
Account                       David Brakman (Plan: Free)
Version                       2.3.35
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040
Forwarding                    http://12345.ngrok.io -> http://localhost:80
Forwarding                    https://12345.ngrok.io -> http://localhost:80
```
The http forwarding url (http://12345.ngrok.io) will be where you, and github, access the Drone server you're about to make.

3. In the Developer Settings for your personal GitHub account, [register a new OAuth application](https://docs.github.com/en/developers/apps/creating-an-oauth-app). 
4. Copy the Client ID and Client Secret to a file on your computer.
5. Specify "Homepage URL": http://12345.ngrok.io
6. Specify "Authorization callback URL": http://12345.ngrok.io/login
7. After finishing the instructions through [Start the Server](https://docs.drone.io/server/provider/github/#start-the-server), **visit http://12345.ngrok.io in your browser**
It should look like ![](./assets/drone-server.png)
