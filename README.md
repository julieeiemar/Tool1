# Tool1
crawling
Beautiful Soup: It is a powerful library for parsing HTML and XML documents. It provides easy-to-use methods to extract data from web pages by traversing the HTML tree structure. Beautiful Soup is widely used for its simplicity and flexibility.
python
Copy code
from bs4 import BeautifulSoup
import requests

# Send a GET request to the URL
response = requests.get('https://example.com')

# Create a Beautiful Soup object
soup = BeautifulSoup(response.content, 'html.parser')

# Find elements using CSS selectors
title = soup.select_one('h1').text
paragraphs = soup.select('p')

# Print the extracted data
print(title)
for p in paragraphs:
    print(p.text)
Scrapy: It is a comprehensive web scraping framework that provides a complete set of tools for crawling and extracting data from websites. Scrapy allows you to define the crawling logic, handle requests and responses, and process the extracted data efficiently.
python
Copy code
import scrapy

class MySpider(scrapy.Spider):
    name = 'example_spider'
    start_urls = ['https://example.com']

    def parse(self, response):
        # Extract data using XPath selectors
        title = response.xpath('//h1/text()').get()
        paragraphs = response.xpath('//p/text()').getall()

        # Process or store the extracted data
        print(title)
        for p in paragraphs:
            print(p)
Selenium: It is primarily used for automating web browsers, but it can also be employed for web scraping tasks. Selenium allows you to interact with web pages, fill forms, click buttons, and perform actions that would be difficult with just HTML parsing.
python
Copy code
from selenium import webdriver

# Set path to chromedriver as per your configuration
webdriver_service = Service('/path/to/chromedriver')

# Choose Chrome browser
browser = webdriver.Chrome(service=webdriver_service)

# Load the web page
browser.get('https://example.com')

# Find elements and extract data
title_element = browser.find_element_by_tag_name('h1')
title = title_element.text

paragraph_elements = browser.find_elements_by_tag_name('p')
paragraphs = [p.text for p in paragraph_elements]

# Process or store the extracted data
print(title)
for p in paragraphs:
    print(p)

# Close the browser
browser.quit()
Remember to review and understand the terms of service and website policies before scraping any website. Additionally, be mindful of any legal and ethical considerations when using web scraping tools.
