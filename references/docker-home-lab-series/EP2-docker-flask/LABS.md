# Labs for EP2 - Dockerizing a Flask App

## Lab 1: Build and Run a Flask App
1. Build the image: `docker build -t flask-app .`
2. Run the container: `docker run -d -p 5000:5000 flask-app`
3. Verify the app at http://localhost:5000

## Lab 2: Optimize the Build Context
1. Add patterns to `.dockerignore` (e.g., `__pycache__/`, `.git/`).
2. Rebuild the image and compare build times.

## Lab 3: Debugging
1. Intentionally introduce an error in `app.py`.
2. Build and run the container.
3. Use `docker logs` to identify the issue.