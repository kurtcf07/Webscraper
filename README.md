Amazon Product Scraper
Overview
This project includes a Python script to scrape product information from Amazon search results pages. The script gathers various details such as product names, brand names, prices, ratings, review counts, and availability, and saves this information to a CSV file. Additionally, a report is generated to provide insights into the data collection process.
Script Explanation
Script: Web_Scraper_Task.ipynb
The script performs the following steps:
Set Headers: Mimic a request from a web browser to avoid being flagged as a bot.
Send Request: Send an HTTP GET request to the Amazon search results page.
Parse Content: Use BeautifulSoup to parse the content of the page.
Extract Links: Find and extract product links from the search results.
Initialize Dictionary: Set up a dictionary to store product details.
Loop Through Links: For each product link:
Send an HTTP GET request to the product page.
Extract product details using various functions.
Append the details to the dictionary.
Create DataFrame: Convert the dictionary to a Pandas DataFrame.
Clean DataFrame: Replace empty product names with NaN and drop rows with missing product names or availability.
Export CSV: Save the cleaned DataFrame to a CSV file with a timestamped filename.
Generate Report: Generate a report summarizing the data collection process and print it.
Functions:
fetch_and_parse(url, headers): Sends a request to the URL and parses the response with BeautifulSoup.
get_Pname(soup): Extracts the product name.
get_Bname(soup): Extracts the brand name.
get_Pprice(soup): Extracts the product price.
get_Prating(soup): Extracts the product rating.
get_Previewcount(soup): Extracts the review count.
get_Stockcheck(soup): Checks the product availability.
get_links(soup): Extracts product links from the search results.
generate_report(amazon_df): Generates a summary report of the data collection process.
Data Justification
Chosen Data Fields:
Product Name: Essential for identifying the product.
Brand Name: Helps in categorizing products by manufacturer.
Price: For price comparison and market analysis.
Product Rating: Indicates customer satisfaction and product quality.
Product Reviews: Reflects the number of customers who have reviewed the product, aiding in assessing product popularity.
Availability: stock status.
Product Link: Useful for direct access to the product page.
On my personal perspective these are the information that I am checking when eyeing for a product in an E-commerce website this will be helpful in comparing products.
Methodology
Data Validation and Cleaning:
Validation: Each function is designed to handle missing data by returning default values (e.g., empty strings) if the expected data is not found.
Cleaning:
Replace empty product names with NaN.
Drop rows where product names or availability are NaN.
Ensure all links are complete URLs.
Analysis:
Extract relevant fields using BeautifulSoup.
Store extracted data in a structured format (dictionary, then DataFrame).
Export data to CSV for further analysis.



Challenges
Encountered Issues and Solutions:
Bot Detection:
 	       Amazon frequently updates its mechanisms to detect bots.
       Solution: Mimic browser headers to make requests appear legitimate.
Dynamic Content:
Amazon's content is often loaded dynamically using JavaScript, making it challenging to scrape static HTML.
Solution: Target HTML elements that are consistently available in the initial page load.
Handling Missing Data:
Some products might lack certain details like ratings or reviews.
Solution: Implement robust error handling in extraction functions to return default values and ensure data integrity.
Request Limitations:
Sending too many requests in a short period can lead to being temporarily blocked.
Solution: Introduce a delay (time.sleep(2)) between requests to avoid triggering anti-bot mechanisms.	
