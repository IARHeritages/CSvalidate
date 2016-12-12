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
pbs --credentials micropasts create_project
```


**NOTE**: In order to use your credentials, create a file in your home folder named .pybossa.cfg and add there a section like this:

[micropasts]
server: http://crowdsourced.micropasts.org
apikey: yourkey

## Updating the project

The previous section created the project, but none of the sections like the template, tutorial, long description or result pages have been populated. To do it, just run the following command:

```
pbs --credentials micropasts update_project
```

While this will work every time you run it, you can save a lot of time by telling pbs to watch for changes in any of those files, so it automatically updates the project for you when you save new changes to any of these files:

*  template.html
*  tutorial.html
*  results.html
*  long_description.md

```
pbs --credentials micropasts update_project --watch
```

## Adding tasks to the project

You can use any of the PYBOSSA CSV or Google Spreadsheet importers, or if you prefer you can use the command line tool to import a CSV or JSON file with tasks for your project:

```
pbs --credentials micropasts add_tasks --tasks-file=example.csv --tasks-type=csv

```

**NOTE**: You can configure the priority and redundancy also, using the command line, check the help.


