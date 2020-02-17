# USE LATEST UBUNTU
FROM ubuntu:latest

# USER & FOLDER SETTINGS
RUN mkdir /home/user
WORKDIR /home/user

# ENVIRONMENT - TO NOT ASK FOR SOME QUESTIONS WHEN INSTALLING
ENV DEBIAN_FRONTEND=noninteractive 

# TIMEZONE - SET TO TBILISI TIMEZONE
ENV TZ='Asia/Tbilisi'
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# UPDATE
RUN apt update

# FEW USEFUL PROGRAMMS
RUN apt install htop tree wget git vim -y
RUN apt install systemd -y

# PYTHON & PIP
RUN apt install build-essential checkinstall libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev zlib1g-dev openssl libffi-dev python3-dev python3-setuptools-y
RUN apt install python3.7 -y
RUN apt install python3-pip -y


# PROJECT FILES
RUN git clone https://your_username:your_password@github.com/path_to_repository

# PROJECT REQUIREMENTS | (FILE IS DIRECTLY IN PROJECT'S FOLDER)
RUN python3.7 -m pip install -r /home/user/your_projects_main_folder/requirements.txt

# START APPLICATION SERVER WHEN WE START A CONTAINER | GUNICORN IS LISTED IN REQUIREMENTS.TXT
CMD cd your_projects_folder && gunicorn --bind 0.0.0.0:5000 wsgi:app
