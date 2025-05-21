### DevOps Assessment Task – JarNox Internship

This is my submission for the JarNox DevOps Internship assessment task. The goal was to set up a basic CI/CD pipeline that automatically deploys a simple Flask app using Jenkins and Codeberg.


### Task Overview
Created a simple Flask app that shows “Hello World” on the homepage

Hosted the code in a Codeberg repository

Installed and configured Jenkins on my local machine

Set up a webhook on Codeberg to trigger Jenkins builds on every push

The Jenkins pipeline:

Pulls the latest code from Codeberg

Installs Flask (using pip install flask)

Restarts the app using a basic shell script


### How I Did It

## 1. Flask App Setup:
I created a basic Flask app in app.py

### Note:
   I did not create a requirements.txt. Instead, I installed Flask manually with:
       pip install flask


## 2. Jenkins Setup
Installed Jenkins on my local machine (Windows/Linux)

Installed Git, Python, and Flask on the system

Set up a freestyle project in Jenkins with the following steps:

Pull code from the Codeberg repo

Install Flask

Restart the Flask app

My shell script (deploy.sh) used in Jenkins:


 - cd ~/Desktop/user/spoorthy
 - git pull origin main
 - pip install flask
 - pkill -f app.py
 - nohup python3 app.py &

Gave the file execute permission:

 - chmod +x deploy.sh


 ## 3. Webhook on Codeberg
Generated a webhook URL from Jenkins (using Git plugin or a webhook trigger plugin)

Added that URL in the Codeberg repo’s settings -> Webhooks section

Now, every push to the main branch automatically triggers Jenkins


### How the Automation Works
 - I pushed new code to Codeberg

 - The webhook informs Jenkins

 - Jenkins pulls the latest code

 - Flask is installed (if not already)

 - The Flask app restarts automatically


### Assumptions & Notes
This setup uses a local Jenkins server, not hosted on the cloud.

I manually installed Flask instead of using requirements.txt to keep things simple.

The app is restarted using a basic pkill + nohup approach. For production, something like systemd, supervisor, or Docker would be more robust.


### Final Notes
 - This task helped me understand how CI/CD works in real time.

 - I learned how Jenkins connects with Git repositories and automates deployments.

 - Looking forward to exploring more advanced tools like Docker and cloud deployment.