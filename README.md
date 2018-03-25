# H-1B Visa Petitions Exploratory Data Analysis

The H-1B is an employment-based, non-immigrant visa category for temporary foreign workers in the United States. Every year, the US immigration department receives over 200,000 petitions and selects 85,000 applications through a random process. The application data is available for public access to perform in-depth longitudinal research and analysis. This data provides key insights into the prevailing wages for job titles being sponsored by US employers under H1-B visa category. In particular, I utilize the 2011-2016 H-1B petition disclosure data to analyze the employers with the most applications, data science related job positions and relationship between salaries offered and cost of living index.

## Data Set Source
The Office of Foreign Labor Certification (OFLC) generates program data that is useful information about the immigration programs including the H1-B visa. The disclosure data updated annually is available at https://www.foreignlaborcert.doleta.gov/performancedata.cfm

- Click on Disclosure Data tab
- Go to Section LCA Programs (H-1B, H-1B1, E-3)
- You will find data from 2008 onwards.

## Requirements
- R
- R Studio
- Packages: readxl, dplyr, hashmap, ggplot2, ggmap, ggrepel

Use `install.packages("package_name")` to install new packages in R.

## Files

- [data_processing.md](data_processing.md): Markdown document illustrating the key data transformations on the raw dataset.
- [data_analysis.md](data_analysis.md): Markdown document illustrating with code for plots and corresponding data analysis.
- [helpers.R](helpers.R): helper functions used mainly for data analysis
- [spell_correcter.R](spell_correcter.R): A suite of functions for performing spell correction in a given vector using the frequencies of occurrence of different elements in the vector.
- [coli/](coli): Python Scrapy code directory for scraping cost of living plus rent index. The [spider crawl file](coli/coli/spiders/coli.py) is the main file describing how the data should be scraped.

## Shiny app
I extended this project to build a Shiny app based on the transformed data set.

- [Explore the app!](https://sharan-naribole.shinyapps.io/h_1b/)

- [GitHub repo](https://github.com/sharan-naribole/H1b_visa_shiny)

## Blogs

Please read my blogs for key data insights and more details:
 - [Data Analysis](https://sharan-naribole.github.io/2017/02/24/h1b-eda-part-I.html)

 - [Shiny app](http://blog.nycdatascience.com/student-works/h-1b-visa-applications-exploration-using-shiny/)

## Kaggle

I have released the transformed dataset on Kaggle for public use under [CC BY-NC-SA 4.0 License](https://creativecommons.org/licenses/by-nc-sa/4.0/).

- [Kaggle Dataset page](https://www.kaggle.com/nsharan/h-1b-visa)

- [Exploration Round One kernel](https://www.kaggle.com/nsharan/d/nsharan/h-1b-visa/exploration-round-one)

## Acknowledgements

- [OFLC Performance data](https://www.foreignlaborcert.doleta.gov/performancedata.cfm)

- [How to Write a Spelling Corrector](http://norvig.com/spell-correct.html)

## License

Open sourced under the [MIT License](LICENSE.md).
