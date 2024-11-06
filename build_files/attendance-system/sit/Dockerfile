FROM node:16 as build
Label stage=build
WORKDIR /app
COPY . .
#RUN npm install
RUN date
RUN node --max-old-space-size=4096 `which npm` install
FROM node:16-alpine
COPY --from=build /app /
EXPOSE 3000
CMD ["node", "app.js"]
#CMD ["npm", "run", "start"]
