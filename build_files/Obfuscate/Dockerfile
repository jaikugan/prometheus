#GST
FROM python:3.8
LABEL stage=builder
WORKDIR /app
RUN pip3 install -r requirements.txt
COPY . .
EXPOSE 5000

# Run the application
CMD [ "uvicorn", "app:app", "--port 3500" ]
