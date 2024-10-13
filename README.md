# Web Scraping Project using Beautiful Soup

This project demonstrates web scraping using Python's Beautiful Soup and `requests` library. We extract useful information from a Stack Overflow question page.

## Objective
The goal of this project is to scrape a specific Stack Overflow page to get the current answers for the question: ["How do I get the current time in Python?"](https://stackoverflow.com/questions/415511/how-do-i-get-the-current-time-in-python)

## Tools and Libraries Used
- **Beautiful Soup**: For parsing HTML and extracting data.
- **Requests**: To fetch the HTML content of the page.
- **Pandas**: To organize the scraped data into a structured format (DataFrame).

## Steps
1. **Fetch HTML Content**:
   - We use the `requests` library to retrieve the webpage's HTML content.
   - Example code:
     ```python
     import requests
     from bs4 import BeautifulSoup as bs
     
     link = 'https://stackoverflow.com/questions/415511/how-do-i-get-the-current-time-in-python'
     page_response = requests.get(url)
     soup = bs(page_response.content, 'html.parser')
     ```
2. **Analyzing the HTML Content and Extracting the Question**:
   - The following code is used to extract the question title from the Stack Overflow page:
     ```python
     question = soup.find('h1')
     question_text = question.text.strip()
     print(question_text)
     
3. **Parse and Extract Answers**:
   - We extract all answers to the question using Beautiful Soup.
   - Code to extract answers:
     ```python
     answers = soup.find_all('div', class_='s-prose js-post-body')
     answer_texts = [answer.text.strip() for answer in answers]
     ```

4. **Organize Data**:
   - We used a Pandas DataFrame to store the extracted answers for easier readability.
     ```python
     import pandas as pd
     df = pd.DataFrame({'Answers': answer_texts})
     print(df)
     ```

## Project Files
- `Weekly_Test_2.ipynb`: The main Python script that handles the web scraping.
- `README.md`: This file explaining the project and its components.

## Requirements
To run this project, install the following libraries:
```bash
pip install requests beautifulsoup4 pandas
