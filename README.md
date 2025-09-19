# 🕸️ Web Scraping Quotes with BeautifulSoup & Selenium

[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![BeautifulSoup](https://img.shields.io/badge/library-BeautifulSoup4-brightgreen)](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
[![Selenium](https://img.shields.io/badge/library-Selenium-orange)](https://www.selenium.dev/documentation/)

A complete **Python project** demonstrating **two approaches to web scraping** —  
**static parsing** with [BeautifulSoup4 (`bs4`)](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)  
and **dynamic browser automation** with [Selenium](https://www.selenium.dev/documentation/) —  
on the practice website: [https://quotes.toscrape.com/](https://quotes.toscrape.com/).

This project extracts:
- ✅ **Quote text**
- ✅ **Author name**
- ✅ **Associated tags**

and saves results to **CSV** and **JSONL** for further analysis.

---

## 📑 Table of Contents
1. [Project Description](#project-description)
2. [Tech Stack](#tech-stack)
3. [Architecture Overview](#architecture-overview)
4. [Installation](#installation)
5. [Repository Structure](#repository-structure)
9. [Output Format](#output-format)
10. [Comparison: BeautifulSoup vs Selenium](#comparison-beautifulsoup-vs-selenium)
11. [Known Issues & Limitations](#known-issues--limitations)
12. [Future Improvements](#future-improvements)


---

## 📘 Project Description
The purpose of this project is to show two industry-standard methods for scraping data:

- **BeautifulSoup (bs4)**:  
  Parses static HTML returned by HTTP requests. Fast, lightweight, and efficient for static pages.

- **Selenium**:  
  Automates a full browser (Chrome). Ideal for scraping pages with heavy **JavaScript rendering**, interactivity, or dynamic content.

The target website is intentionally designed for learning:  
👉 [https://quotes.toscrape.com/](https://quotes.toscrape.com/)

---

## ⚙️ Tech Stack
| Category         | Technology                                                                 |
|------------------|-----------------------------------------------------------------------------|
| Language         | Python 3.8+                                                                 |
| Libraries        | `requests`, `beautifulsoup4`, `selenium`, `webdriver-manager`, `csv`, `json`|
| Browser Driver   | Google Chrome / Chromium + ChromeDriver                                     |
| Output Formats   | CSV, JSONL                                                                  |
| Environment      | Works locally and in Google Colab                                           |

---

## 🏗️ Architecture Overview
```text
 ┌─────────────────────┐      ┌───────────────────────────────┐
 │  BeautifulSoup Path │      │  Selenium Path                │
 │─────────────────────│      │───────────────────────────────│
 │ requests → HTML GET │      │ webdriver.Chrome() launch     │
 │ BeautifulSoup parse │      │ Browser automation (headless) │
 │ Extract text/tags   │      │ DOM navigation via selectors  │
 │ Stop after N quotes │      │ Click “Next” until N quotes   │
 └─────────────────────┘      └───────────────────────────────┘
              │                                  │
              └───────────────┬──────────────────┘
                              ▼
                    Save results → CSV / JSONL

```
##🔧 Installation
-**1. Clone the repository**
git clone https://github.com/your-username/web-scraping-quotes-bs4-selenium.git
cd web-scraping-quotes-bs4-selenium

-**2. Create & activate virtual environment (recommended)**
python3 -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows

-**3. Install dependencies**
pip install -r requirements.txt


**requirements.txt**

requests
beautifulsoup4
selenium
webdriver-manager



## 📂 Repository Structure
web-scraping-quotes-bs4-selenium/
├── Web Scrapping.ipynb          # implementation
├── README.md              # Documentation
├── data/
│   ├── quotes_10_bs4.csv
│   ├── quotes_100_bs4.csv
│   ├── quotes_10_selenium.csv
│   └── quotes_100_selenium.csv



## 📊 Output Format

-**CSV example:**

text,author,tags
"The world as we have created it is a process of our thinking...",Albert Einstein,change,deep-thoughts,thinking,world
"It is our choices, Harry, that show what we truly are...",J.K. Rowling,abilities,choices


-**JSONL example:**

{"text": "The world as we have created it...", "author": "Albert Einstein", "tags": ["change","deep-thoughts"]}
{"text": "It is our choices, Harry...", "author": "J.K. Rowling", "tags": ["abilities","choices"]}


## 📐 Comparison: BeautifulSoup vs Selenium


| Feature                | BeautifulSoup (bs4)                 | Selenium                                       |
| ---------------------- | ----------------------------------- | ---------------------------------------------- |
| **Speed**              | ⚡ Fast (parses static HTML)         | 🐢 Slower (runs a browser instance)            |
| **Dependencies**       | Lightweight (`requests`, `bs4`)     | Heavy (browser, driver, `selenium`)            |
| **Dynamic JS Content** | ❌ Cannot handle JS rendering        | ✅ Full support (executes JS, clicks, scrolls)  |
| **Use Cases**          | Static websites, APIs, simple pages | Dynamic sites, JS-heavy pages, form automation |



## 🚀 Future Improvements

Add unit tests for both scrapers.

Provide a Dockerfile for environment consistency.

Add parallel scraping for speed (async requests).

Implement retry logic & robust error handling.

Extend scrapers to books.toscrape.com for practice.
