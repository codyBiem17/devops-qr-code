# set base image with alpine linux
FROM python:alpine3.17

#set working directory
WORKDIR /app

#install pip package
RUN python -m pip install --upgrade pip

#copy the requirements.txt file from host machine to docker image working directory
COPY requirements.txt .

#install dependencies from requirements.txt file
RUN pip install --no-cache-dir -r requirements.txt

#copy the rest of the application files from local
COPY . .

#expose application on a port
EXPOSE 8000

#run the server
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
