# News-Trendz
## News Sentiment Analysis & Entity Extraction

[LOOK AT THE CODE AND EXECUTE ](https://colab.research.google.com/drive/1VqfNkeH7uCY1wiPU-Hsqy2r5jWHDHp7G?usp=sharing)

## Output
- **DataFrame Output:** Displays the articles, their metadata, extracted entities, sentiment scores, and keywords.
- **Visualizations:** Shows trends in sentiment, keywords, locations, and organizations appearing in the news.

## 23 February 2025 | Monday | 23:00 PM

| ![image](https://github.com/user-attachments/assets/862207b3-2eb4-40ff-a3c7-8b0830965a45) | ![image](https://github.com/user-attachments/assets/517ee437-da64-4fe2-984e-574a90069859) |
|---|---|
| ![image](https://github.com/user-attachments/assets/22b4558b-ea80-4dd8-bb3f-4b6e35a944fb) | ![image](https://github.com/user-attachments/assets/148b44a4-a0c9-4748-aa49-53f6736af3bd) |
| ![image](https://github.com/user-attachments/assets/39874db9-a6aa-421b-b8cd-681b49bd0b3e) | ![image](https://github.com/user-attachments/assets/0b0bc933-d9a1-4bfa-a620-191b5915c276) |
| ![image](https://github.com/user-attachments/assets/a03cb793-f6d3-49c9-91ee-54c52bbe2aa4) | ![image](https://github.com/user-attachments/assets/e6848b32-e53b-4a54-b843-4e2070d8af87) |

## Overview
This project fetches news articles from multiple sources, extracts their content, and performs sentiment analysis and named entity recognition (NER). It then visualizes the sentiment distribution, top keywords, locations, and organizations mentioned in the news.

## Features
- **Fetch news articles** from various Indian news sources.
- **Extract article content** using BeautifulSoup.
- **Perform Named Entity Recognition (NER)** using SpaCy.
- **Analyze sentiment** using NLTK's SentimentIntensityAnalyzer.
- **Generate visualizations** to show trends in sentiment, keywords, and named entities.

## Requirements
Ensure you have Python installed along with the following dependencies:
```bash
pip install nltk requests pandas beautifulsoup4 spacy pytz matplotlib seaborn altair plotly geopandas wordcloud
```
Additionally, download the necessary NLTK and SpaCy models:
```python
import nltk
nltk.download('vader_lexicon')
import spacy
spacy.cli.download("en_core_web_sm")
```

## Usage
### 1. Load Required Libraries
```python
import nltk
import requests
import pandas as pd
import xml.etree.ElementTree as ET
from datetime import datetime
import pytz
from bs4 import BeautifulSoup
import spacy
from nltk.sentiment import SentimentIntensityAnalyzer
from collections import Counter
from IPython.display import display
```
### 2. Initialize Models
```python
nlp = spacy.load("en_core_web_sm")
sia = SentimentIntensityAnalyzer()
```
### 3. Fetch News Articles & Analyze Sentiment
```python
def Fetch_Articles_Metadata(channel_names, channels_xml_links):
    ... # Fetch and process news data
    return pd.DataFrame(data)

# Define news sources
channel_names = ["The Hindu", "Hindustan Times", "NDTV", "News18", "Zee News", "Jagran", "Firstpost", "Indian Express", "LiveMint", "Business Standard", "India.com", "Indiatoday", "Bhaskar", "DNA India"]
channels_xml_links = [
    ["https://www.thehindu.com/sitemap/googlenews/all/all.xml"],
    ["https://www.hindustantimes.com/sitemap/news.xml"],
    ... # Other sources
]

# Fetch Data
df = Fetch_Articles_Metadata(channel_names, channels_xml_links)
display(df)
```
### 4. Visualize Results
```python
import matplotlib.pyplot as plt
import seaborn as sns
from wordcloud import WordCloud

if not df.empty:
    # Sentiment Analysis Bar Chart
    plt.figure(figsize=(8, 5))
    sns.countplot(x='Sentiment', data=df, palette={"Positive": "green", "Neutral": "gray", "Negative": "red"})
    plt.title("Sentiment Analysis of News Articles")
    plt.xlabel("Sentiment")
    plt.ylabel("Number of Articles")
    plt.show()

    # Word Cloud for Keywords
    wordcloud_text = " ".join(df['Keywords'].dropna())
    wordcloud = WordCloud(width=800, height=400, background_color='black', colormap='coolwarm').generate(wordcloud_text)
    plt.figure(figsize=(10, 5))
    plt.imshow(wordcloud, interpolation="bilinear")
    plt.axis("off")
    plt.title("Top Keywords in News Articles")
    plt.show()
```

## Future Enhancements
- Add more news sources.
- Improve Named Entity Recognition (NER) for better classification.
- Use machine learning models for more advanced sentiment analysis.
- Implement a web-based dashboard for interactive analysis automated.
