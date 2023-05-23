SubsScraper
---------

Run command for generate urls
```commandline
search
search search.cnt=2 # for 2 urls
search 'search.query="лекции таймкоды"' search.cnt=2 # override cyrillic (more quotes)
```

Run command for subscrape urls
```commandline
subscrape
search scraper.audio_format=mp3 # convert to audio format
search scraper.lvl=text # download only text
```

Default configs
```commandline
search:
  output_folder: data
  result_file: urls.txt
  cnt: 10
  query: машинное обучение лекции таймкоды

scraper:
  output_folder: ${search.output_folder}/dataset
  audio_format: m4a
  lvl: audio # text, audio, video
```

timecoder.py - is a pipeline for division uploaded subtitles to blocks based on threshold of cosinus similarity

Inside the script there are 2 approaches:
1) first summarization of subtitles followed by calculation of cosinus similarity
2) first calculation of cosinus similarity followed by division by blocks and then summarization of each block

parse_subs.py - is a parser of YouTube subtitles converting them to pd.DataFrame
sentence_similarity.py - script for calculation of cosinus similarity
gpt_shortening.py - script for summarization

Different models for summarization and Sentence Similarity were compared. For similarity now we are using "IlyaGusev/mbart_ru_sum_gazeta". For Sentence Similarity the model called 'symanto/sn-xlm-roberta-base-snli-mnli-anli-xnli'.

