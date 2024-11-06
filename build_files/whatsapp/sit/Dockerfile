From node:16 as build
LABEL stage=build
WORKDIR /app
COPY . .   
RUN npm install
#RUN node --max-old-space-size=4296 `which npm` install
FROM node:16-alpine
COPY --from=build /app /
EXPOSE 4292
#CMD {"node --max-old-space-size=4296 app.js"}
CMD ["node", "server.js"]

