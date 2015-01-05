FROM 3dot/node:latest
MAINTAINER Miran Hojnik <docker@3dot.net>

#Install sails.js as global
RUN npm -g install sails

#Set env var to port 1337 for sails, and expose the port to host
ENV PORT 1337
EXPOSE 1337

#Run sails.js
WORKDIR /data/app
CMD ["nodejs", "app.js"]