#PT
FROM --platform=linux/amd64 python:3.8.6
LABEL stage=build
WORKDIR /app

RUN apt-get update
RUN apt-get install -y curl apt-transport-https
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/debian/10/prod.list > /etc/apt/sources.list.d/mssql-release.list
RUN apt-get update
RUN ACCEPT_EULA=Y apt-get install -y msodbcsql17 unixodbc-dev

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt
RUN pip3 install gunicorn
# clean the install.
RUN apt-get -y clean

COPY . .
EXPOSE 8000
# Run the application
CMD ["gunicorn","-b","0.0.0.0:8000","elaitia.app:app" ]
#CMD ["waitress-serve","elaitia.app:app"]
