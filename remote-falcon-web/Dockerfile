FROM node:16.14.0-alpine as build
WORKDIR /app
ENV PATH /app/node_modules/.bin:$PATH
COPY package.json ./
COPY package-lock.json ./
RUN npm ci --silent
RUN npm install react-scripts@3.4.1 -g --silent
RUN npm install serve -g --silent
RUN npx browserslist@latest --update-db
COPY . ./

RUN npm run build


# start the nginx web server
CMD ["serve", "-s", "/app/build"]
