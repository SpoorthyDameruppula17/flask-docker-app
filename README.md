# DevOps Internship Assignment – CI/CD with Jenkins and Codeberg

Hi! This is my submission for the DevOps assessment task at JarNox. The goal of this project was to build a simple CI/CD pipeline using **Jenkins** and **Codeberg**, to automatically deploy a basic **Flask "Hello World"** app.



##  What I Built

A simple Flask web app that returns "Hello World" on the homepage. Every time I push new code to the Codeberg repository, Jenkins automatically pulls the code, installs dependencies, and redeploys the app. I used **Docker** to make deployment clean and consistent.



##  Project Structure

 - app.py # Flask application
 - Dockerfile # For containerizing the app
 - requirements.txt # Flask dependency
 - jenkins-pipeline.sh # Script Jenkins runs on each build



---

## How the Automation Works

1. **Code Push to Codeberg**  
   I push my code changes to the Codeberg repo.

2. **Webhook Trigger**  
   I set up a webhook in Codeberg that hits my Jenkins server when there's a new push.

3. **Jenkins Pipeline**  
   Jenkins receives the webhook, pulls the latest code, and runs a shell script:
   - Installs the Python dependencies from `requirements.txt`
   - Builds the Docker image
   - Stops and removes any old containers
   - Runs the app in a fresh container

Now the app is live again with the new changes — all automatically.



## How to Test It

After the setup, open a browser and go to `http://localhost:5000` or your server IP. You’ll see **“Hello World”**.



### Assumptions & Notes
- I assumed the Jenkins server is running on a public IP or tunnel (e.g., ngrok) so the webhook can reach it.

- I used Docker to make app deployment easy, but it could also be done without Docker.

- The app is basic just to test automation, not for production use.


### Thanks!
Thanks for the opportunity! This task helped me understand real-world CI/CD better, and I enjoyed working on it. 

