# Use an existing dokcer image a base
FROM node:alpine

WORKDIR /usr/app

# only runn npm install if package.json is changed
COPY ./package.json ./

# Download and install a dependencies

RUN npm install

# copy code to container

COPY ./ ./

# Default container
CMD ["npm", "start"]