# Sample Fullstack Application

## Description

A simple ToDo application with frontend in Next.js and backend in Nest.js 

## Prerequisites
* Docker Engine
* Docker compose

## Command to run Project
- Refereing to `sample.env`, create a file `.env`:
```bash
Illustration:

DATABASE_URL=postgres://postgres:helloworld@db:5432/db_01
REDIS_URL=redis://redis:6379
POSTGRES_PASSWORD=helloworld
POSTGRES_DB=db_01
BACKEND_BASE_URL=http://localhost:5000
```
- Open terminal in root directory: 
```bash
$ docker-compose build
```

```bash
$ docker-compose build
```

- And you are ready to go!
- Access the application at:
```bash
http://localhost:3000
```

## Stats
- Total size combined occupied by the Frontend and Backend images on disk: 1.08 GB

- Total size occupied by all 4 images together: 1.54 GB

- On GitHub, the sizes of the frontend and backend images are 238 MB and 174 MB, respectively

## Points covered
- Docker files have multiple build stages to reduce the size of the image
- The reason for using the Alpine version is to reduce the size of the image, as Alpine versions are minimalistic
- Backend Dockerfile has been integrated with tests  

## Points not covered
- Volumes not used for persistent storage of data (but can be used via docker-compose.yml file)
- Separate branches can be created for frontend and backend pipeline, so that image updates only during update
