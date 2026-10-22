# Dockerfile — package the Evergreen Quote API into a container image (Starter)
# ----------------------------------------------------------------------------
# A Dockerfile is a recipe. Each instruction adds a LAYER to the image. Fill in
# the TODOs by following the lab guide, then build and run the container.

# TODO 1: start from an official, small Node base image.
#   FROM node:22-alpine
FROM scratch

# Set the working directory inside the image.
WORKDIR /app

# TODO 2: copy package.json first (so dependency install is cached separately
#         from your source code), then install only production dependencies.
#   COPY package.json ./
#   RUN npm install --omit=dev

# TODO 3: copy the rest of the application source into the image.
#   COPY . .

# Document the port the app listens on.
EXPOSE 3000

# TODO 4: the command that runs when the container starts.
#   CMD ["node", "src/index.js"]
