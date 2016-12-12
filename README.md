# CSvalidate
Crowdsourcing template to validate the content of webpages 

# Installation

First you will need to install all the dependencies with the following commands:

```bash

virtualenv env
source env/bin/activate
pip install -r requirements.txt
```

This process will create a virtual environment for hosting all the PYBOSSA required libraries. This will be in a folder named **env** and each time you need to use them, you will have to activate it with the second command (source env/bin/activate).

# Creating the project

In order to create the project in a PYBOSSA server, you have to run the following command:

```
pbs --credentials YOURCREDENTIALS create_project
```


