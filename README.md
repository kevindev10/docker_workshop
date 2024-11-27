# Docker Workshop

Welcome to the Docker Workshop repository! This project is designed to help students understand and implement containerization using Docker. The repository includes all the resources, examples, and exercises you need to get started with Docker.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Workshop Outline](#workshop-outline)
- [Dockerfile Explained](#dockerfile-explained)
- [Usage](#usage)
- [Pushing to Docker Hub](#pushing-to-docker-hub)
- [Exercises](#exercises)
- [Contributing](#contributing)
- [License](#license)

---

## Introduction

Docker is a platform for developers and sysadmins to develop, deploy, and run applications with containers. Containers allow you to package an application with all its dependencies into a standardized unit for software development.

This workshop provides hands-on exercises and examples to help you learn the fundamentals of Docker, including building, running, and managing containers.

---

## Prerequisites

Before you begin, ensure you have the following installed on your system:

1. **Docker**: Install Docker by following the instructions on the [official Docker website](https://docs.docker.com/get-docker/).
2. **Git**: Ensure you have Git installed to clone this repository. Get Git from [here](https://git-scm.com/).
3. **Docker Hub Account**: Create a free Docker Hub account at [hub.docker.com](https://hub.docker.com/) if you don’t already have one.

---

## Getting Started

1. **Clone this repository**:

   ```bash
   git clone https://github.com/kadimasum/docker_workshop.git
   cd docker_workshop
   ```

2. **Navigate to the project folder**:

   ```bash
   cd docker_workshop
   ```

3. **Run the first example**:

   Follow the instructions provided in the workshop files.

---

## Workshop Outline

### 1. **Introduction to Docker**
   - What is Docker?
   - Benefits of containerization.
   - Docker architecture.

### 2. **Setting Up Docker**
   - Installing Docker.
   - Running your first container.

### 3. **Building and Managing Containers**
   - Creating a Dockerfile.
   - Building images.
   - Running containers from images.
   - Managing containers with Docker commands.

### 4. **Working with Docker Compose**
   - Introduction to Docker Compose.
   - Creating `docker-compose.yml` files.
   - Running multi-container applications.

### 5. **Real-World Application**
   - Building and deploying a Django application using Docker.

---

## Dockerfile Explained

The `Dockerfile` is a text file that contains a set of instructions to build a Docker image. Here's how the `Dockerfile` in this repository was created and how it works:

### Example `Dockerfile`

```Dockerfile
# Step 1: Use an official Python base image
FROM python:3.9-slim

# Step 2: Set the working directory inside the container
WORKDIR /app

# Step 3: Copy the requirements file to the container
COPY requirements.txt .

# Step 4: Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Step 5: Copy the rest of the application code
COPY . .

# Step 6: Expose the application port
EXPOSE 8000

# Step 7: Define the command to run the Django application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

### Explanation of the `Dockerfile`

1. **Base Image (`FROM`)**:
   - The `FROM` instruction specifies the base image for the container. In this case, it uses the official Python 3.9 slim image to keep the container lightweight.

2. **Set Working Directory (`WORKDIR`)**:
   - The `WORKDIR` instruction sets the working directory inside the container where all subsequent commands will be executed. Here, `/app` is used.

3. **Copy Requirements File (`COPY`)**:
   - The `COPY requirements.txt .` command copies the `requirements.txt` file (containing Python dependencies) into the working directory.

4. **Install Dependencies (`RUN`)**:
   - The `RUN pip install` command installs all the dependencies listed in the `requirements.txt` file.

5. **Copy Application Code (`COPY`)**:
   - The second `COPY . .` command copies the rest of the application code into the container.

6. **Expose Port (`EXPOSE`)**:
   - The `EXPOSE` instruction specifies the port that the Django application will run on. Here, it’s port `8000`.

7. **Run the Application (`CMD`)**:
   - The `CMD` instruction defines the command to start the Django application when the container runs. It runs the development server with `python manage.py runserver 0.0.0.0:8000`.

---

## Usage

### Build an Image

```bash
docker build -t django-app .
```

### Run a Container

```bash
docker run -d -p 8000:8000 django-app
```

### Stop a Container

```bash
docker stop <container_id>
```

### Remove a Container

```bash
docker rm <container_id>
```

---

## Pushing to Docker Hub

Follow these steps to push your Docker image to Docker Hub:

1. **Log In to Docker Hub**:
   Log in to Docker Hub using the `docker login` command. Provide your Docker Hub username and password when prompted.

   ```bash
   docker login
   ```

2. **Tag the Docker Image**:
   Tag your Docker image with the format `username/repository:tag`. Replace `username` with your Docker Hub username, `repository` with the name of the repository you want to create on Docker Hub, and `tag` with a version or descriptive label (e.g., `latest`).

   ```bash
   docker tag django-app your_dockerhub_username/django-app:latest
   ```

3. **Push the Image to Docker Hub**:
   Use the `docker push` command to upload your tagged image to Docker Hub.

   ```bash
   docker push your_dockerhub_username/django-app:latest
   ```

4. **Verify the Image on Docker Hub**:
   Visit your Docker Hub account, navigate to the repository, and confirm that your image is listed.

---

## Exercises

Each section in the workshop includes exercises to help reinforce the concepts covered. Complete them step-by-step, and feel free to ask questions if you get stuck.

Example Exercise:

- Create a `Dockerfile` for a simple Django application.
- Build an image and run the application in a container.
- Push the image to Docker Hub.

---

## Contributing

Contributions are welcome! Feel free to fork this repository, submit issues, or create pull requests.

To contribute:

1. Fork this repository.
2. Create a new branch: `git checkout -b feature/my-feature`.
3. Make your changes and commit them: `git commit -m 'Add some feature'`.
4. Push to the branch: `git push origin feature/my-feature`.
5. Open a pull request.

---

## License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

