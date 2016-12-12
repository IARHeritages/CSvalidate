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

**WARNING**: Be sure to have your virtualenv active. Use the source command, when you need it.


**NOTE**: In order to use your credentials, create a file in your home folder named .pybossa.cfg and add there a section like this:

```
[micropasts]
server: http://crowdsourced.micropasts.org
apikey: yourkey

```

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

## Adding tasks to the project from a CSV file

You can use the command line tool to import a CSV or JSON file with tasks for your project:

```
pbs --credentials micropasts add_tasks --tasks-file=example.csv --tasks-type=csv

```

It is really important that the column name with the URL for the page or web link, should be named **url**, otherwise the template will fail. 

**NOTE**: You can configure the priority and redundancy also, using the command line, check the help.

## Adding tasks from a Google Form

Create a google form, and add as many questions as you want. It is really important that each question is just one word in lowercase, this will ensure that we will be able to render them properly in the template.

For this specific project the only required field is the **URL** of the page, so the Google form should have one question with a name: url.

See for example this one: https://goo.gl/forms/UD4RAkA9a6FDQpt73


Be sure to configure the Form to save the responses in a Google Spreadsheet, as we will be using that file to import the submitted responses as tasks for the current project.

Once you have the Google Form ready, go to the responses tab, and check the "View responses in Sheets":

![Imgur](http://i.imgur.com/z71C3Aq.png)

That will open the spreadsheet. Go to the sharing options, and make it public for anyone having the link: click in Get shareable link. Then, choose: Anyone with the link can view.  Then copy that link, and paste it in the PYBOSSA Google Spreadsheet importer. That will import the submitted responses.

**NOTE**: If you can set up an auto-importer, you will be able to automatically import data into your project thanks to PYBOSSA. Go to task settings, auto-importers, choose the Google Spreadsheet and paste the URL. Depending if you are a regular user or a pro, the project will get the new responses every 24 hours or 10 minutes.


