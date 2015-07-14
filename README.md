This project wiki describes Northbridge agile team processes.

This project code is responsible for the interactions between Northbridge agile team processes and GitHub issues tracking.

There are three major components to this project: web interface, export, and import. These are represented as the yellow components of this diagram.

Web Interface: Allows Northbridge volunteers to estimate and select user stories from a prioritized backlog of work.

Export: When invoked, export all Backlog User Stories in state "Selected" from the database to a GitHub Issues list using the GitHub API.

Import: When invoked, update a Backlog User Story to Accepted. This process will respond to a GitHub Issues Webhook.

![Project Diagram](http://northbridgetech.org/images/alliance2.jpg)

Installation
============

::
	sudo apt-get install python-pip

If you want to use a virtual environment you must do something like (Ubuntu):
::
	pip install virtualenvwrapper
	# Go to the project directory
	mkvirtualenv playbook
	# The next command is only necessary if you are not already using the created virtualenv
	workon playbook

To install the dependencies you could do something like this (Ubuntu):
::
	pip install -r requirements.txt

Database settings are located in the playbook/settings.py file and must be updated to represent your local environment.

If you do not already have the database structure you must run django migrate scripts:
::
	# Note that running the following commands will create an empty database (No projects, teams, backlogs, volunteers etc)
	python manage.py makemigrations
	python manage.py migrate

Create a superuser
::
	python manage.py createsuperuser

Running
=======

::
	python manage.py runserver [host:port]

Now you can go to <host>:<port>/admin and login using the user created above. You can create groups and users.
