# Codebook
Below we list each dataset and describe the relevant variables
## `book_purchase_data.Rdata`
This file contains one dataset called `collection_event_time` which contains information on purchases of award winning children's books near the time of award announcement.  
To create this dataset, we use data on book purchases between 2017-2020 from the Numerator Omni-panel.  
We manually match each award winning children's book in our sample (published between 2016 and 2019) with the item_ids of book purchased in this data by title. 
Then we use purchases of all other books in the children's department that were published between 2016 and 2019 as our comparison group.

We first identify the date each book was eligible for an award (the yearly awards in our sample are are announced near the end of January and only books published the year before are eligible).
Then we count the number of purchases of each book per day, centered around the award announcement date in the year each book was eligible.
We then find the average purchases of books in a collection/citation category per day.

The variables in this dataset and their descriptions are as follows:
  - `collection_citation`: The collection (e.g. Mainstream or Diversity) and the citation (e.g. Award Winners or Award Honors)
  - `event_time`: number of days since award annoucement in the year a book was eligible
  - `quantity_purchased_scaled`: average number of purchases for books in a given collection_citation and in a given event time
  - `moving_average_quantity_purchased_scaled`: 14-day moving average of `quantity_purchased_scaled`

## `cces_data.Rdata`
This file contains one dataset called `cces` which contains data from the Cooperative Election Study (CCES), a nationally representative, stratified sample survey administered by YouGov. The survey collects information about general political attitudes linked with respondent demographic data. We draw from the 2017 CCES data set because it was the earliest survey year for which book purchase data were available. We collapse this data to the zip code level.

The variables in this dataset and their descriptions are as follows:
  - `postal_code`: 5-digit zip code
  - `pct_deport`: percentage of respondents surveyed in a zip code who think the U.S. government should identify and deport illegal immigrants
  - `pct_angry`: percentage of respondents surveyed in a zip code who somewhat or strongly agree with the statement "I am angry that racism exists"
  - `pct_advantage`: percentage of respondents surveyed in a zip code who somewhat or strongly agree that White people in the U.S. have certain advantages because of the color of their skin
  - `pct_fund`: percentage of respondents surveyed in a zip code who think the U.S. government should withhold federal funds from localities that do not follow federal immigration laws

## `census_data.Rdata`
This file contains one dataset called `census_data` which contains the estimated proportion of individuals in the United States that belong to a given age, gender, or race category as determined by the U.S. census in a given by decade.

The variables in this dataset and their descriptions are as follows:
  - `decade`: decade the census estimates are from
  - `group`: the identity of interest (e.g. child, female, etc)
  - `group_pct`: the proportion of the population that belong to `group` in `decade`
  - `total_group`: the total number of people that belong to `group` in `decade`
  - `total_population`: the total number of people in the U.S. in `decade`
  - `collection`: data source (all observations indicate that this information is from the U.S. Census, but this variable is useful when merging with representation data)
  - `type`: the indentity type that `group` variable corresponds to (e.g. `type=Gender` when `group=Female`)

## `library_data.Rdata`
This file contains five datasets called `award_dates`, `branches`, `checkouts`, `inventory`, and `sample_books`.

### award_dates
This dataset contains the date that the American Library Association Awards (ALA) in our sample are announced. This date is tied to the ALA Midwinter Meetings which are held in January every year (though the exact date differs)

The variables in this dataset and their descriptions are as follows:
  - `award_year`: the year the award was announced
  - `award_date`: the date of the ALA Midwinter Meetings where the awards are announced

### branches
This dataset contains demographics for community reporting areas (CRA) in Seattle and information on the books in their public libraries. We manually matched each CRA to its closest Seattle Public Library branch. Each Seattle Public Library branch is matched to at least one CRA. Population demographics are taken from the American Community Survey, 5-year Series 2013-2017 accessed through Seattle's Data Portal. Seattle Public Library inventory data as reported on October 1st, 2017 also accessed through Seattle's Data Portal.

The variables in this dataset and their descriptions are as follows:
  - `item_location`: Seattle Public Library branch
  - `cra_name`: the community reporting area in Seattle matched to a given Seattle Public Library branch
  - `total_population`: the total population of a given community reporting area (`cra`) in Seattle 
  - `pct_nothisp_white_one`: proportion of the community reporting area (`cra`) in Seattle that is white, non-hispanic
  - `pct_population_under_poverty`: proportion of the population that is below the poverty line in a given community reporting area (`cra`) in Seattle 
  - `median_hh_inc_past_12mo_dollar`: median household income in the past 12 months for a given community reporting area (`cra`) in Seattle
  - `total_books`: the total number of children's books in a given Seattle Public Library branch
  - `mainstream`: the total number of award winning children's books that belong to the Mainstream collection in a given Seattle Public Library branch
  - `diversity`: the total number of award winning children's books that belong to the Diversity collection in a given Seattle Public Library branch

### checkouts
This dataset contains data on library book checkouts from 2005-2017 from the Seattle Public Library open data portal.

The variables in this dataset and their descriptions are as follows:
  - `bib_num`: the unique identifier given to the book by the Seattle Public Library
  - `item_type`: type of book as defined [here](https://data.seattle.gov/Community/Integrated-Library-System-ILS-Data-Dictionary/pbt3-ytbc)
  - `publication_year`: estimated year the book was published
  - `checkout_date_time`: the date and time of checkout

### inventory
This dataset contains information on the number of copies of award winning children's books each library branch has in their inventory. This data was creating using Seattle Public Library inventory data as reported on October 1st, 2017 accessed through Seattle's Data Portal.

The variables in this dataset and their descriptions are as follows:
  - `bib_num`: the unique identifier given to the book by the Seattle Public Library
  - `collection`: the collection a given award winning book belongs to
  - `item_location`: Seattle Public Library branch
  - `item_count`: the number of copies of a given book that belong to a given Seattle Public Library branch

### sample_books
This dataset contains a crosswalk between library bib_nums which we have identified as one of the award winning books in our sample and the collection the book belongs to as well as the books citation and the year it was recognized by an award.

The variables in this dataset and their descriptions are as follows:
  - `collection`: whether the award winning book belongs to the Mainstream or Diversity collection
  - `citation`: whether the book won an award or was honored
  - `bib_num`: the unique identifier given to the book by the Seattle Public Library
  - `year_meta`: the year the book was recognized by an award
  - `winner`: a boolean (True/False) variable indicating whether the book won an award (as opposed to being honored)

## `representation_data.Rdata`
This file contains two datasets called `book_level_data` and `image_level_data`.

### `book_level_data`
The variables in this dataset and their descriptions are as follows:

### `image_level_data`
The variables in this dataset and their descriptions are as follows:

## `search_interest_data.Rdata`  
This file contains one dataset called 

The variables in this dataset and their descriptions are as follows:

## `censored_data/book_purchase_level_data.Rdata`
This file contains one dataset called 

The variables in this dataset and their descriptions are as follows:
