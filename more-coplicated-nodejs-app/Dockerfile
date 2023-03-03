FROM node:12-stretch 

USER node

WORKDIR home/node/code

# these copy commands are chached. So this till prevent npm install from running, unless something gets changed in package-lock.json or package.jsopn
# this concept is called "layers" 
# the only call out on this - is that if minor patch versions get updated, running npm install would result in a minor version update, 
# but since this will hit a cache layer, npm install will never run and not get the security patch
COPY --chown=node:node package-lock.json package.json ./

RUN npm ci

COPY --chown=node:node . .


CMD [ "node", "index.js" ]