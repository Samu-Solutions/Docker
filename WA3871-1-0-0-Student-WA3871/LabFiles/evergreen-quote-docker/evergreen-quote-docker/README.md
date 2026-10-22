# Evergreen Quote API - Containerization with Docker (Starter)

Package the Evergreen Quote API (the standalone Express server from Week 2 of
Phase 3) into a **Docker container**: a portable, self-contained unit that runs
the same way on any machine. You will write the `Dockerfile`, build the image,
and run it.

## Run it

Docker is installed on your lab VM. From this folder:

```bash
# 1. Build the image (after you finish the Dockerfile)
docker build -t evergreen-quote-api .

# 2. Run a container from it, mapping host port 3000 to the container's 3000
docker run --rm -p 3000:3000 evergreen-quote-api

# 3. In another terminal, hit the API
curl http://localhost:3000/api/quotes
```

Complete the `TODO`s in the `Dockerfile` first, following the lab guide.
