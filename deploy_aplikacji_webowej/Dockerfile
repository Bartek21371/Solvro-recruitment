##Stage of building
#Set image node.js 20 Lts Slim
FROM node:20-slim AS builder
 
#Install Git
RUN apt-get update && apt-get install -y git

#Define working directory
WORKDIR /app

#Clone repo
RUN git clone https://github.com/Solvro/web-solvro-docs.git .

#Install dependencies by using npm
RUN npm pkg set 'allowScripts.sharp=true' \
    npm ci \
    npm run build \


##Stage of serve

#Set image of nginx
FROM nginx:stable AS serve

#Copy dist
COPY --from=builder /app/dist /usr/share/nginx/html

#Port to expose
EXPOSE 80

#CMD
