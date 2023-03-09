# Base image
FROM node:14-alpine

#Change work directory
WORKDIR /usr/app

#  ---- This causes Unnecessary rebuilds, even if file that does not affect 'npm install' is changed ----
# Copy build files
# COPY ./ ./
# Install dependencies
# RUN npm install

#  ---- Minimizing rebuilds ----
# Copy first what takes long to build, but changed really rarely, and independent on the rest of files
COPY ./package.json ./
# Build
RUN npm install
# Then copy things which do not require long rebuilds (also, can be rebuilt separately of previous files), but changed frequently
COPY ./ ./

# Default command
CMD [ "npm", "start" ]