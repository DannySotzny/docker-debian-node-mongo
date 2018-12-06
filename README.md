# Docker Image with NodeJS 6 + MongoDB

***plus the Tools git, screen and curl***

# How to Use in your own Dockerfile
If you use this in your own Dockerfile then start the MongoDB Service with screen!
To ensure that the mongoDB is up before you start you app please use wait-for-it

add this to your `Dockerfile`: 

    ADD https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh /app/bin/wait-for-it.sh
    RUN chmod +x /app/bin/wait-for-it.sh

and then start like this:

    CMD  screen -dmS mongo /usr/bin/mongod --config /etc/mongod.conf && bin/wait-for-it.sh localhost:27017 -t 10 -- node yourApp.js

`screen` will start the mongoDB in an extra terminal and with wait-for-it your App will start if the port is open. In my Example a node app `yourApp.js`
btw: my App is located in `/app`

## special Branch ret
here i install mono and the  poppler-utils additional