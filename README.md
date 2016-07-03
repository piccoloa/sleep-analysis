# sleep-analysis
A Python project to analyze my Fitbit sleep data.

## Overview
This is a Python 3 project to obtain and analyze data on my sleep patterns, which has been collected nightly since July 2015 on my Fitbit Charge HR. My primary goal for this project is to gain insight into my sleep patterns -- ambiguous, yes, but at the time I started the project, I did not know what I would learn. Secondary goals include learning to use Fitbit's API and the OAuth 2.0 protocol, understanding how to work with large datasets, and introducing myself to Junyper notebooks.

This project has two key components. The first part is the data collection, which was done through use of the Fitbit API and a Python script. The second part is the data analysis, which will (probably) be done through a Junyper notebook rendered in this repository.

Note: Fitbit is a registered trademark and service mark of Fitbit, Inc. My sleep analysis project is designed for personal use with the Fitbit platform. This product is not put out by Fitbit, and Fitbit does not service or warrant the functionality of this product.x

---

## Part 1: Obtaining Minute-by-Minute Sleep Data
The first part of this project involves accessing my nightly, minute-by-minute sleep data from Fitbit's servers. Fitbit does not usually provide this through their smartphone or desktop apps; users can only generally see summary statistics. In order to access them, I had to use Fitbit's API and request it directly from their servers.

### Instructions
Clone the repo, and create a new file called `secrets.py` (you will notice that this is listed in .gitignore). This file should contain the following (secret) constants:

	CLIENT_ID = ''
	CLIENT_SECRET = ''
	AUTH_CODE = ''

These will be filled in later. Go to the [Fitbit Developers website](https://dev.fitbit.com/), register for an account, and register an app with them. The app will be for "Personal" use, as this will give access to intraday sleep data. Enter your Client ID and Client Secret into `secrets.py`. Now, go to the URL:

	https://www.fitbit.com/oauth2/authorize?response_type=code&client_id=XXXXXX&scope=sleep

replacing 'XXXXXX' with your Client ID, and authorize your app to access your sleep data. You will be redirected to the website you entered upon registration, with an additional code at the end of the URL (taking the form `?code=_____`); enter this code in `secrets.py`.

Finally, you are ready to run the app from the command line as `python fitbit.py \<start date\>`, with `\<start date\>` being optional, formatted as `yyyy-mm-dd`. This will write up to 150 days' worth of minute-by-minute sleep data to the directory `/logs/`.

### Usage Notes
Fitbit limits API usage to 150 requests per hour. If you have more than 150 days of data, the script will write 150, then exit and tell you the start date for the top of the next hour.

If the start date is not entered, a default date of 150 days ago is chosen.

All libraries used are part of Python's standard library.

---

## Part 2: Data Analysis
Coming soon!