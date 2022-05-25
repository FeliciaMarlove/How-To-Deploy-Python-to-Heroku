# How To Deploy Python to Heroku
Cheatsheet to deploy a Python app to Heroku (used to deploy a Discord bot for free)
This procedure is suited for an already existing code base that was using another git service already.
A Heroku account and app must be created beforehand.

## Install gunicorn in your Python project 
It's a worker to run a Python web app, used by Heroku
```
pip install gunicorn
```

## Install Heroku on your local machine
This will allow you to use the command line interface for further steps.
[Get the installer here](https://devcenter.heroku.com/articles/getting-started-with-python#set-up)


## Login to Heroku
```
heroku login
```

## In your project, configure Heroku remote
A deployment of the app will happen every time you push on this repository.
```
heroku git:remote -a discord-bot-harmegnies
```

## Generate the requirements.txt (at project root)
This file will inform Heroku about the dependencies and versions to use.
```
pip freeze > requirements.txt
```

## Add the Procfile (at project root)
The file name is "Procfile", case sensitive!
This file containes the commands executed at startup.
```
web: gunicorn <your-python-application-boot-file>.wsgi
```
![image](https://user-images.githubusercontent.com/57141210/170202898-dca96df2-ecf0-4c46-8152-b111665896f3.png)


## Push the code
```
git push heroku master
```
