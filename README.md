# BooksScrapping


## Getting Started

### Prerequisites
Ensure you have the following installed:
- Python 3.x (Download from [python.org](https://www.python.org/downloads/))
- Jupyter Notebook (Included with Anaconda or install separately)
- Git

### Installation

1. **Install Dependencies:**
   
    Install the required packages:
    ```sh
    pip install -r requirements.txt
    ```
    ex: python -m pip install --upgrade pip
        pip install BeautifulSoup
        pip install pandas as pd

### Running the Scraper
1. **Open Jupyter Notebook:**
    ```sh
    jupyter notebook
    ```

2. **Run the Notebook:**
    Open `books_scraper.ipynb` in the Jupyter interface and run the cells to execute the scraping code.

### Example Usage
The Jupyter Notebook contains the following steps:
1. **Loading the HTML file:**
    ```python
    with open('books_to_scrape.html', 'r', encoding='utf-8') as file:
        html_content = file.read()
    ```

2. **Parsing the HTML content:**
    ```python
    from bs4 import BeautifulSoup
    soup = BeautifulSoup(html_content, 'html.parser')
    ```

3. **Extracting Data:**
    ```python
    book_data = []
    for book in soup.find_all('article', class_='product_pod'):
        title = book.h3.a['title']
        price = book.find('p', class_='price_color').text
        availability = book.find('p', class_='instock availability').text.strip()
        book_data.append({'title': title, 'price': price, 'availability': availability})
    ```

