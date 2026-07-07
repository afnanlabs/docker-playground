# Lab Answers for EP2 - Dockerizing a Flask App

## Lab 1: Build and Run a Flask App
- `docker build -t flask-app .` creates an image tagged `flask-app`.
- `docker run -d -p 5000:5000 flask-app` runs the app in detached mode.
- Verify by visiting http://localhost:5000.

## Lab 2: Optimize the Build Context
- Adding patterns like `__pycache__/` and `.git/` to `.dockerignore` reduces the build context size.
- Rebuilding the image is faster with a smaller context.

## Lab 3: Debugging
- Logs from `docker logs <container_id>` reveal the error.
- Fix the error in `app.py` and rebuild the image.