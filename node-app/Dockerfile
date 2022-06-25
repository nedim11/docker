# Use Node.js version 9.9.0 as a base image.
FROM node:9.9.0

# Create a directory (run as a root user).
RUN mkdir -p /home/node/app

# Grants ownership over the app dir to node:node (run as a root user).
RUN chown -R node:node /home/node/app

# Makes newly created dir a working dir.
WORKDIR /home/node/app

# Copies the current directory (root dir) into the WORKDIR in the container.
COPY --chown=node:node . ./

# Run later steps as the 'node' user (unprivileged user that comes built into all of the official node images from Docker) instead of root (security hardening).
USER node

# Enter WORKDIR and run 'yarn install' as a 'node' user which is going to install our dependencies.
RUN yarn install

# Exposes port 8081.
EXPOSE 8081

# Once we created our build, we can run our Node.js application. So here, "node" is going to run out app.js.
CMD ["node", "/home/node/app/index.js"]
