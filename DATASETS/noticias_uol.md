# Notícias UOL
## Exploration

Fazer uma sumarização das notícias.
- Provavelmente será possível fazer uma validação da sumarização.
- Tentar agrupar palavras diferentes mas que possam significar a mesma coisa em um dado contexto.
- "Reescrever" a notícia com base na sumarização de forma mais simples.

### Initial Code

```python
>> import numpy as np
>> import pandas as pd
>> import spacy
>> df = pd.read_csv("dataset/articles.csv")[:500]
>> nlp = spacy.load("pt_core_news_sm")
>> import pt_core_news_sm
>> nlp = pt_core_news_sm.load()
>> doc = nlp(df.iloc[0].text)
```
```python
>> from collections import Counter
# print([{w.text: w.pos_} for w in doc])
>> Counter([w.pos_ for w in doc])
Counter({'NOUN': 108,
         'VERB': 83,
         'PUNCT': 82,
         'ADP': 78,
         'PROPN': 44,
         'DET': 42,
         'PRON': 39,
         'SCONJ': 38,
         'NUM': 23,
         'ADV': 22,
         'ADJ': 21,
         'AUX': 14,
         'CCONJ': 14,
         'SPACE': 12,
         'INTJ': 1})
```
```python
>> # Counter de adjetivos
>> Counter([w.text for w in doc if w.pos_ == "ADJ"])
Counter({'segunda': 2,
         'eleitoral': 2,
         'acostumados': 2,
         'lascado': 1,
         'expressivo': 1,
         'penais': 1,
         'alternativo': 1,
         'próximos': 1,
         'rápido': 1,
         '1º': 1,
         'agressivo': 1,
         'brasileira': 1,
         'últimas': 1,
         '"': 1,
         'ensaia': 1,
         'econômico': 1,
         'simpático': 1,
         'financeiro': 1})
```


## Dataset Info
### About

The dataset consists of 167.053 examples and contains Headlines, Url of Article, Complete Article and Category. I gathered the summarized news from Inshorts and only scraped the news articles from Folha de São Paulo - http://www.folha.uol.com.br/ (Brazilian Newspaper). Time period ranges is between January 2015 and September 2017.

### Credits

https://www.kaggle.com/datasets/marlesson/news-of-the-site-folhauol
https://github.com/marlesson/scrapy_folha