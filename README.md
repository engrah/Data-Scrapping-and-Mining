# Data-Scrapping-and-MiningData Scraping with Python: BeautifulSoup and PandasThis repository contains a Python project for scraping data from websites using BeautifulSoup and Pandas. The project demonstrates how to extract specific information from a webpage, process it, and store it in a structured format like CSV.Table of ContentsIntroductionInstallationProject StructureUsage
Step 1: Identify the Target Website
Step 2: Write the Python Script
Step 3: Run the Script
Step 4: View the ResultsContributingLicenseIntroductionThis project provides a simple example of web scraping using Python.
We utilize two powerfullibraries:BeautifulSoup: For parsing HTML and extracting the required data
Pandas: For storing and manipulating the data in a tabular format, and exporting it to a CSV file.InstallationTo get started, clone this repository and 
install the required Python libraries.Clone the Repositorygit clone https://github.com/yourusername/data-scraping-example.git
cd data-scraping-exampleInstall Python LibrariesEnsure you have Python installed. Then, install the necessary libraries using pip: 

# HERE THE PYTHON CODE
pip install requests beautifulsoup4 pandas


Project Structuredata-scraping-example/
│
├── scrape_contacts.py        # Main Python script for scraping data
├── README.md                 # This readme file
├── requirements.txt          # Python dependencies
└── contacts.csv              # The output file (generated after running the script)scrape_contacts.py: The Python script that performs the web scraping
contacts.csv: The CSV file where the scraped data will be saved.UsageFollow these steps to scrape data from a webpage

# Step 1: Identify the Target WebsiteFind the webpage you want to scrape. For this example, let's assume you're scraping contact details (names and emails) from a business directory.

# Step 2: Write the Python ScriptOpen the scrape_contacts.py file and modify it to suit your target website. Here’s a template to get you started:

# HERE we inport these 2 libraries 
import requests
from bs4 import BeautifulSoup
import pandas as pd

# URL of the webpage to scrape
url = 'https://www.example.com/directory'  # Replace with the actual URL

# Send a GET request to the website
response = requests.get(url)

# Check if the request was successful
if response.status_code == 200:

# Parse the HTML content
    soup = BeautifulSoup(response.text, 'html.parser')
    
 # Lists to store the scraped data
    names = []
    emails = []
    
 # Extract data from the HTML
    for item in soup.find_all('div', class_='contact-info'):  
    
# Adjust based on HTML structure
        name = item.find('h2', class_='name').text.strip()
        email = item.find('a', class_='email').text.strip()
        
        names.append(name)
        emails.append(email)
    
 # Create a DataFrame
    df = pd.DataFrame({
        'Name': names,
        'Email': emails
    })
    
# Save the DataFrame to a CSV file
    df.to_csv('contacts.csv', index=False)
    
    print('Data saved to contacts.csv')
else:
    print(f'Failed to retrieve the page. Status code: {response.status_code}')
    
# Step 3: Run the ScriptAfter editing the script with the correct URL and HTML tags, run the script:python scrape_contacts.py

# Step 4: View the ResultsThe script will generate a contacts.csv file containing the scraped data. You can open this file in Excel, Google Sheets, or any text editor to view the results.ContributingIf you'd like to contribute, feel free to fork the repository and submit a pull request with your improvements.LicenseThis project is licensed under the MIT License - see the LICENSE file for details.
