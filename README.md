# WordPress Docker Lab

## Table of Contents
1. [Quickstart](#quickstart)
2. [Usage](#usage)
3. [Configuration](#configuration)

## Project Overview
This repository contains a minimal WordPress setup running in Docker using docker-compose.

## Quickstart
1. Make sure Docker Desktop is installed and running.
2. Clone this repository.

```bash
   git clone https://github.com/ibog1/-wordpress-docker-lab.git
   cd -wordpress-docker-lab
   ```
3. Run `docker compose up -d`.
```bash
docker compose up -d
```
4. Open `http://localhost:8080` in your browser and complete the WordPress installation wizard.

5. Complete the WordPress installation wizard and create an admin user.
  You can then log in at `http://localhost:8080/wp-admin`.


## Usage

This section describes how to start, stop and test the WordPress Docker setup.

### Starting and stopping the stack

Start the containers in the background:
```bash
docker compose up -d
```

Stop the containers but keep the data:

```bash
docker compose down
```

Completely remove containers and volumes (all data will be removed):

```bash
docker compose down -v
```


### Verifying data persistence

1. Log in to the WordPress admin at `http://localhost:8080/wp-admin`.
2. Create a visible test post (for example *“DevSecOps Persistence Test”*) and publish it.
3. Restart the stack:

```bash
docker compose down
```
```bash
docker compose up -d
```

4. Open `http://localhost:8080` again and verify that the test post is still present.  
If the post is still visible, the database and WordPress files are correctly persisted in Docker volumes.

## Configuration

The stack is defined in `docker-compose.yaml` and uses environment variables from an `.env` file.

### Environment variables

An example configuration is provided in [`example.env`](example.env).

1. Copy the example file
2. Edit `.env` and set your own database credentials and passwords.
3. Start the stack with:

```bash
docker compose up -d
```

In `docker-compose.yaml` both services reference these variables via `env_file` and `${VAR}` syntax, so no credentials are stored directly in the compose file.
