# all Dockerfiles start with a from instruction. This specifies the base image from which we are building our docker container
FROM node:12-stretch

# without this, the process is running as the root user of the container with access to everything
USER node

WORKDIR /home/node/code

# --chown=user:group
COPY --chown=node:node index.js index.js

# Add will auto unzip a file or tar file. It will also reach out to the network and download anything
#ADD --chown=node:node index.js index.js

RUN npm ci

CMD ["node", "index.js"]



# How to build and run this container 
# docker build -t my-node-app .

# --init lets you control c out of the container since node doesnt know how to do this 
# --rm removes it after you close it 
# --publish 3000:3000 exposes the container and lets it run node on port 3000. We use this since this container does not have auto access to the host network 

#docker run --init --rm --publish 3000:3000 my-node-app