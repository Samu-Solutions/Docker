# Evergreen Quote API - Containerization with Docker (Solution)

The completed reference. The `Dockerfile` packages the Express API into an image.

```bash
docker build -t evergreen-quote-api .
docker run --rm -p 3000:3000 evergreen-quote-api
# In another terminal:
curl http://localhost:3000/api/quotes
```
