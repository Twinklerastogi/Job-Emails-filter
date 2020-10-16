# Job-Emails-filter
#### Scraping emails from an existing email address on the basis of their subject containing keywords "Thank you for applying" and categories them into a "job" category.

You will need to download a credentials-gmail.json file by going to https://developers.google.com/gmail/api/quickstart/python and clicking the Enable the Gmail API button (after logging in to your Gmail account). You will need to rename the downloaded credentials-gmail.json file to credentials.json.

#### Requirements
* Python
* A Google account with Gmail enabled
* Beautiful Soup library
* Google API client and Google OAuth libraries

#### Installation 
Install the required libraries by running these commands

* pip install –upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib
* pip install beautifulsoup4

#### Approach
The file 'token.pickle' contains the User's access token. If it does not exist, program open the browser and ask for access to the User's Gmail and save it. Now, we will connect to the Gmail API with the access token. This will return a list of IDs of the last 100 emails (default). We can ask for any number, output of this request is a dictionary.

This dictionary contains 'headers', 'parts', 'filename', etc. The key 'parts' contains all the parts of Email's such as text, HTML, Attached file details, etc. The body is encoded in Base 4 encoding, we have to convert it to a readable format. After decoding, the obtained text is in 'lxml'. So, we will parse it using the BeautifulSoup library and convert it to text format.

At last, we will use FuzzyWuzzy library. It is a string matching process of finding strings that match a given string or pattern. Basically, it uses Levenshtein Distance to calculate the difference between sequences.

