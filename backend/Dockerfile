FROM node:18 AS build 
WORKDIR /app
COPY package*.json ./
RUN npm install --only=production
COPY . .


#satge--2
FROM node:18-alpine AS production
WORKDIR /app
COPY --from=build /app ./
EXPOSE 5000
CMD ["node" , "server.js"]
