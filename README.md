# All_about_Docker

## Table of Contents:
- [Dockerizing Your Django Project](#dockerizing-your-django-project)
- [Running Dockerized Django Project on Another PC](#running-dockerized-django-project-on-another-pc)


## Dockerizing Your Django Project

### Step 1: Docker Installation
Make sure you have Docker installed on your system. You can download and install Docker from the official Docker website [here](https://www.docker.com/get-started).

### Step 2: Dockerfile
Create a Dockerfile in the root directory of your Django project. The Dockerfile is a text file that contains instructions for building a Docker image.

```Dockerfile
# Use an official Python runtime as the base image
FROM python:3.9

# Set the working directory in the container
WORKDIR /app

# Copy the requirements.txt file to the container
COPY requirements.txt .

# Install the Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code to the container
COPY . .

# Expose the port that Django runs on (default is 8000)
EXPOSE 8000

# Start the Django development server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

### Step 3: requirements.txt
Create a requirements.txt file in the root directory of your Django project. This file should contain all the Python dependencies required by your project. You can generate this file using the command `pip freeze > requirements.txt` in your project's virtual environment.

### Step 4: Build the Docker Image
Open a terminal, navigate to the directory where your Dockerfile is located, and run the following command to build the Docker image:

```
docker build -t myblog .
```

This command will build a Docker image with the tag "myblog" using the current directory as the build context.

### Step 5: Run the Docker Container
Once the image is built, you can run a Docker container using the following command:

```
docker run -p 8000:8000 myblog
```

This command maps port 8000 of the container to port 8000 on your host machine, allowing you to access the Django development server running inside the container.

### Step 6: Access the Django Application
Open your web browser and visit http://localhost:8000 to access your Django blog application running inside the Docker container.

By following these steps, you should be able to dockerize your Django blog project and run it in a Docker container. Docker provides a portable and consistent environment for running your application, making it easier to deploy and manage across different systems.

## Stopping a Docker Container

To stop a running Docker container, you can use the `docker stop` command. Here's how:

1. Open a terminal or command prompt.

2. Run the following command to list the running Docker containers:
```
docker ps
```

3. Identify the container you want to stop from the list. Note the container ID or name associated with it.

4. Use the following command to stop the container:
```
docker stop <container_id_or_name>
```
Replace `<container_id_or_name>` with the actual container ID or name of the container you want to stop.

5. Wait for a few seconds until the container stops. You can confirm that the container has stopped by running the `docker ps` command again and checking if the container is no longer listed.

By following these steps, you can stop a running Docker container. Stopping a container gracefully allows it to clean up and exit properly. If you want to force-stop a container immediately without allowing it to clean up, you can use the `docker kill` command instead of `docker stop`.

```
## Running Dockerized Django Project on Another PC

To run your Dockerized Django blog project on another PC, you'll need to follow these steps:

1. **Install Docker**: Make sure Docker is installed on the new PC. You can download and install Docker from the official Docker website [here](https://www.docker.com/get-started).

2. **Copy the Project Files**: Transfer the Dockerized Django blog project files to the new PC. This includes the Dockerfile, project code, and any other necessary files.

3. **Build the Docker Image**: Open a terminal or command prompt, navigate to the project directory (where the Dockerfile is located), and run the following command to build the Docker image:

   ```
   docker build -t myblog .
   ```

   This command will build a Docker image with the tag "myblog" using the current directory as the build context. Make sure to run this command within the project directory where the Dockerfile is located.

4. **Run the Docker Container**: Once the Docker image is built, you can run a Docker container using the following command:

   ```
   docker run -p 8000:8000 myblog
   ```

   This command maps port 8000 of the container to port 8000 on the new PC's host machine, allowing you to access the Django development server running inside the container.

5. **Access the Django Application**: Open a web browser on the new PC and visit [http://localhost:8000](http://localhost:8000) to access your Django blog application running inside the Docker container.

By following these steps, you should be able to run your Dockerized Django blog project on the new PC. Docker provides a portable and consistent environment, allowing you to easily deploy and run your application on different systems without worrying about dependencies or configurations.
```

