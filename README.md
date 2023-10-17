# Homework 1 - Professionalism & Reproducibility

This repository contains the Homework 2 for DATA 512 Human Centered Data Science

The goal of this assignment is to explore the concept of bias in data using Wikipedia articles. The assignment will consider articles about cities in different US states. For this assignemnt we combine a dataset of wikipedia articles with a dataset of state populations, and use a machine learning service called ORES to estimate the quality of the articles about the cities.

## Data Sources

The data for this project is extracted using the Wikipedia API. The information was collected using a Category of the Wikipedia Articles.

- [Wikipedia Category: Lists of Cities in the United States by State](https://en.wikipedia.org/wiki/Category:Lists_of_cities_in_the_United_States_by_state)
- [US Census Bureau Population Estimates](https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html)
- List of US Regions - spreadsheet in the repository

## Repository Structure:

```bash
.
├── data_acquisition.ipynb
├── data_analysis.ipynb
├── README.md
├── LICENSE
├── input-data
│   ├── NST-EST2022-POP.xlsx
│   ├── US States by Region - US Census Bureau.xlsx
│   └── us_cities_by_state_SEPT.2023.csv
├── intermediate-data
│   ├── cities_article_quality.csv
│   ├── cities-info.json
├── data
│   ├── wp_scored_city_articles_by_state.csv
├── example-code
│   ├── wp_ores_liftwing_example.ipynb
│   ├── wp_page_info_example.ipynb
```

## Input Data
- **NST-EST2022-POP.xlsx** - Excel file that contains the population estimates of every state by the US Census Bureau

- **US States by Region - US Census Bureau.xlsx** - Excel file that contains the region demarcation of states into regions defined by the US Census Bureau

- **us_cities_by_state_SEPT.2023.csv** - CSV file that contains the crawled wikipedia url and article_title for every city within each state.

## Intermediate Data

- **cities-info.json** - JSON file that is saved as the output from the wikipedia page info code to get the revision_id and page info for every city in the state.

- **cities_article_quality.csv** - CSV file that is saved as the output from the ORES API code to get the article and quality score for each article.

## Data

**wp_scored_city_articles_by_state.csv** - The CSV file that contains the article info, population and article quality. This file is used for the analysis

### Data Description

- **state**: the state of the article
- **regional_division**: the region of the state given by US Census Bureau
- **population**: the population estimate of 2022 given by the US Census Bureau for each state
- **article_title**: the title in the form of 'city, state'
- **revision_id**: the last revision_id extracted from wikipedia API
- **article_quality**: the article quality for each article extracted from the ORES API

## Code

- `data_acquisition.ipynb` - Python Notebook that uses the APIs to extract the data and perfoms the necessary processing steps (removing duplicates, NA values and non-states)

- `data_analysis.ipynb` - Python Notebook that uses the final data file to perform the analysis.

## Research Implications

Through our analysis, we have revealed a range of insights and potential biases within the dataset. Notably, even in well-resourced countries like the United States, geographical biases become apparent.

### What are the Potential Biases ?

Population bias is a common type of bias, where areas with larger populations tend to attract more attention and receive more comprehensive coverage. Editorial bias, on the other hand, emerges from the open contribution platform of Wikipedia and is influenced by the demographics of its editors, impacting the depth of coverage on specific topics. Another noticeable bias is historical bias, characterized by more detailed articles dedicated to historically significant cities or those marked by major events. Geographical bias can arise from the proximity of regions to media centers or areas with higher internet penetration. Additionally, temporal bias becomes apparent as recent events often garner more coverage, even when their long-term significance remains uncertain.

### Wikipedia as a Data Source ?

Utilizing Wikipedia as a data source presents a spectrum of advantages and challenges. It hinges on crowdsourced knowledge, which can yield both accuracy and neutrality or bias, contingent on contributors. The platform's openness makes it vulnerable to vandalism and misinformation, although there are established safeguards. It's important to note that not all information is meticulously cited, potentially leading to inaccuracies in research. Furthermore, articles may exhibit variations in detail and perspective influenced by the primary contributors' language and cultural context. Wikipedia's dynamic nature is advantageous for accessing current information, yet it poses challenges due to evolving data baselines.

### Where does this Data Remains Useful ?

Notwithstanding these obstacles, Wikipedia data retains its significance in preliminary research, serving as a comprehensive launchpad. The ever-evolving nature of Wikipedia positions it as an excellent tool for trend analysis, offering insights into the emergence of new trends and shifts in public interest. Even in the presence of inherent data biases, making relative comparisons, such as assessing the coverage of two cities, can yield valuable insights. Wikipedia's articles, with their diverse content, offer valuable perspectives on culture and society. Furthermore, Wikipedia frequently acts as a historical repository, preserving events and developments as they unfold.

### How might a researcher transform this dataset ?

To mitigate the limitations and biases observed in the dataset, a researcher could consider several approaches. First, supplementing the dataset with additional sources of information, such as government records, independent surveys, or academic databases, can help provide a more comprehensive and balanced perspective. Second, implementing data preprocessing techniques, including text analysis and entity resolution, can assist in identifying and rectifying biases in the dataset. Furthermore, by applying machine learning algorithms and statistical methods, it's possible to adjust for certain biases, such as population bias or geographical bias, in the analysis. Finally, transparency in reporting any potential biases and the steps taken to address them is essential in maintaining research integrity and ensuring that data limitations are appropriately addressed.

## Licence

This project is licensed under the MIT License. Please see the LICENSE file for more details.