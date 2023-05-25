# CODEBOOK

# Public Data
Below we list each dataset and describe the relevant variables.

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

### `award_dates`
This dataset contains the date that the American Library Association Awards (ALA) in our sample are announced. This date is tied to the ALA Midwinter Meetings which are held in January every year (though the exact date differs)

The variables in this dataset and their descriptions are as follows:
  - `award_year`: the year the award was announced
  - `award_date`: the date of the ALA Midwinter Meetings where the awards are announced

### `branches`
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

### `checkouts`
This dataset contains data on library book checkouts from 2005-2017 from the Seattle Public Library open data portal.

The variables in this dataset and their descriptions are as follows:
  - `bib_num`: the unique identifier given to the book by the Seattle Public Library
  - `item_type`: type of book as defined [here](https://data.seattle.gov/Community/Integrated-Library-System-ILS-Data-Dictionary/pbt3-ytbc)
  - `publication_year`: estimated year the book was published
  - `checkout_date_time`: the date and time of checkout

### `inventory`
This dataset contains information on the number of copies of award winning children's books each library branch has in their inventory. This data was creating using Seattle Public Library inventory data as reported on October 1st, 2017 accessed through Seattle's Data Portal.

The variables in this dataset and their descriptions are as follows:
  - `bib_num`: the unique identifier given to the book by the Seattle Public Library
  - `collection`: the collection a given award winning book belongs to
  - `item_location`: Seattle Public Library branch
  - `item_count`: the number of copies of a given book that belong to a given Seattle Public Library branch

### `sample_books`
This dataset contains a crosswalk between library bib_nums which we have identified as one of the award winning books in our sample and the collection the book belongs to as well as the books citation and the year it was recognized by an award.

The variables in this dataset and their descriptions are as follows:
  - `collection`: whether the award winning book belongs to the Mainstream or Diversity collection
  - `citation`: whether the book won an award or was honored
  - `bib_num`: the unique identifier given to the book by the Seattle Public Library
  - `year_meta`: the year the book was recognized by an award
  - `winner`: a boolean (True/False) variable indicating whether the book won an award (as opposed to being honored)

## `representation_data.Rdata`
This file contains two datasets called `book_level_data` and `image_level_data`. These datasets contain information on representation in the text and images of the award winning books in our sample.

### `book_level_data`
This dataset contains information on representation at a book level.
The variables in this dataset and their descriptions are as follows:
  - `decade`: the decade in which a given award winning book won an award
  - `collection`: the collection a given award winning book belongs to (e.g. Mainstream, Diversity, or a sub-collection of the Diversity collection)
  - `pct_monochromatic`: the percent of faces in a given book which are classified as being monochromatic
  - `mean_skin_tint`: the average skin tint of the representative skin color of all faces detected in a given book
  - `pct_polychromatic_1st`: the percent of faces with polychromatic representative skin colors in the first skin tint tercile within a given book
  - `pct_polychromatic_2nd`: the percent of faces with polychromatic representative skin colors in the second skin tint tercile within a given book
  - `pct_polychromatic_3rd`: the percent of faces with polychromatic representative skin colors in the third skin tint tercile within a given book
  - `unique_famous_people`: the number of unique famous people identified in a given book
  - `mentions_famous_people`: the number of mentions of famous people in a given book
  - `pct_mentions_famous_female`: the percent of mentions of famous people that are female in a given book
  - `pct_unique_famous_females`: the percent of unique of famous people that are female in a given book
  - `unique_famous_asian`: the number of unique famous people that are asian in a given book
  - `unique_famous_black`: the number of unique famous people that are black in a given book
  - `unique_famous_indigeneous`: the number of unique famous people that are indigeneous in a given book
  - `unique_famous_latinx`: the number of unique famous people that are latinx in a given book
  - `unique_famous_multiracial`: the number of unique famous people that are multiracial in a given book
  - `unique_famous_white`: the number of unique famous people that are white in a given book
  - `unique_famous_asian_female`: the number of unique famous people that are asian females in a given book
  - `unique_famous_asian_male`: the number of unique famous people that are asian males in a given book
  - `unique_famous_black_female`: the number of unique famous people that are black females in a given book
  - `unique_famous_black_male`: the number of unique famous people that are black males in a given book
  - `unique_famous_indigenous_female`: the number of unique famous people that are indigeneous females in a given book
  - `unique_famous_indigenous_male`: the number of unique famous people that are indigeneous males in a given book
  - `unique_famous_latinx_female`: the number of unique famous people that are latinx females in a given book
  - `unique_famous_latinx_male`: the number of unique famous people that are latinx males in a given book
  - `unique_famous_multiracial_female`: the number of unique famous people that are multiracial females in a given book
  - `unique_famous_multiracial_male`: the number of unique famous people that are multiracial males in a given book
  - `unique_famous_white_female`: the number of unique famous people that are white males in a given book
  - `unique_famous_white_male`: the number of unique famous people that are white females in a given book
  - `pct_unique_famous_asian`: the percent of unique famous people identified that are asian in a given book
  - `pct_unique_famous_black`: the percent of unique famous people identified that are black in a given book
  - `pct_unique_famous_indigeneous`: the percent of unique famous people identified that are indigeneous in a given book
  - `pct_unique_famous_latinx`: the percent of unique famous people identified that are latinx in a given book
  - `pct_unique_famous_multiracial`: the percent of unique famous people identified that are multiracial in a given book
  - `pct_unique_famous_white`: the percent of unique famous people identified that are white in a given book
  - `pct_mentions_famous_asian`: the percent of mentions famous people that are asian in a given book
  - `pct_mentions_famous_black`: the percent of mentions famous people that are black in a given book
  - `pct_mentions_famous_indigeneous`: the percent of mentions famous people that are indigeneous in a given book
  - `pct_mentions_famous_latinx`: the percent of mentions famous people that are latinx in a given book
  - `pct_mentions_famous_multiracial`: the percent of mentions famous people that are multiracial in a given book
  - `pct_mentions_famous_white`: the percent of mentions famous people that are white in a given book
  - `pct_child_faces`: the percent of faces detected that are predicted to be children in a given book
  - `pct_female_faces`: the percent of faces detected that are predicted to be female in a given book
  - `pct_asian_faces`: the percent of faces detected that are predicted to be asian in a given book
  - `pct_black_faces`: the percent of faces detected that are predicted to be black in a given book
  - `pct_latinx_others_faces`: the percent of faces detected that are predicted to be latinx or other race in a given book
  - `pct_white_faces`: the percent of faces detected that are predicted to be white in a given book
  - `pct_asian_female_faces`: the percent of faces detected that are predicted to be asian females in a given book
  - `pct_asian_male_faces`: the percent of faces detected that are predicted to be asian males in a given book
  - `pct_black_female_faces`: the percent of faces detected that are predicted to be black females in a given book
  - `pct_black_male_faces`: the percent of faces detected that are predicted to be black males in a given book
  - `pct_latinx_others_female_faces`: the percent of faces detected that are predicted to be female and latinx or other race  in a given book
  - `pct_latinx_others_male_faces`: the percent of faces detected that are predicted to be male and latinx or other race in a given book
  - `pct_white_female_faces`: the percent of faces detected that are predicted to be white females in a given book
  - `pct_white_male_faces`: the percent of faces detected that are predicted to be white males in a given book
  - `young_male_terms`: the percent of gendered terms that are young and male in a given book
  - `old_male_terms`: the number of gendered terms that are old and male in a given book
  - `young_female_terms`: the number of gendered terms that are young and female in a given book
  - `old_female_terms`: the number of gendered terms that are old and female in a given book
  - `pct_young_gendered_terms`: the percent of gendered terms that are young in a given book
  - `pct_female_words`: the percent of gendered words that are female in a given book (gendered words = gendered terms + gendered + names)
  - `pct_female_names`: the percent of names that are predicted to be female in a given book
  - `book_ID`: the unique identifier given to a book

### `image_level_data`
This dataset contains information on representation at an image level.
The variables in this dataset and their descriptions are as follows:
  - `collection`: the collection the award winning book belongs to (e.g. Mainstream, Diversity, or a sub-collection of the Diversity collection)
  - `decade`: decade that the book this face belongs to won an award
  - `skin_tint`: skin tint of a face's representative skin color 
  - `rgb_sd`: the standard deviation between the red, green, and blue values of the RGB representation of a face's representative skin color.
  - `hex`: hex code representing a face's representative skin color in RGB space
  - `image_color`: image color categorization of a face's representative skin color (e.g. monochromatic, polychromatic, non-typical)
  - `gender`: predicted gender of a given face
  - `age_group`: predicted age group of a given face
  - `race`: predicted race of a given face
  - `face_ID`: unique identifier given to a face

## `search_interest_data.Rdata`  
This file contains one dataset called `google_trends`:
The variables in this dataset and their descriptions are as follows:
  - `date`: date corresponding to the first day of the week that the search interest is measured in
  - `collection`: whether the award winning book belongs to the Mainstream or Diversity collection
  - `interest`: search interest
  - `year`: year the search interest is was collection

# Censored Data
Data on book purchases between 2017-2020 comes from the Numerator Omnipanel. We use this data to construct table II, table III, table Vb, table VI, and figure Ib. The authors are not permitted to share these data, but we do share the code we use to create the relevant tables and figures. Below we list each censored dataset and describe the relevant variables.

## `censored_data/book_purchase_level_data.Rdata`
This file contains one dataset called `purchases`.
The variables in this dataset and their descriptions are as follows:
  - `collection`: the collection the award winning book belongs to (e.g. Mainstream, Diversity, or a sub-collection of the Diversity collection)
  - `postal_code`: 5 digit zip code where the book was purchased
  - `book_ID`: unique identifier for an award winning book in our sample
  - `item_id`: unique identifier for an item purchased in the Numerator Omnipanel data
  - `item_total`: total amount spent on the item
  - `item_quantity`: number of items purchased
  - `item_unit_price`: unit price on the item
  - `trip_id`: unique identifier for a shopping trip
  - `gender_app_user`: gender of the purchaser
  - `parent_child_gender`: gender of the parent and gender of their child
  - `ethnicity`: ethnicity of the purchaser
  - `lgbtq`: sexual orientation of the purchaser
  - `lgbtq_sexual_orientation`: sexual orientation of the purchaser
  - `has_children`: whether the purchaser has children
  - `has_children_ages_0_5`: whether the purchaser has children between 0 and 5
  - `has_children_ages_6_12`: whether the purchaser has children between 6 and 12
  - `has_children_ages_13_17`: whether the purchaser has children between 13 and 17
  - `income_bucket`: income bucket of purchaser
  - `education_group`: highest education completed by purchaser
  - `has_son_expand`: whether the purchaser has a son
  - `has_both_expand`: whether the purchaser has a son and a daughter
  - `has_daughter_expand`: whether the purchaser has a daughter
  - `mean_skin_tint`: mean skin tint of faces in book purchased
  - `pct_female_faces`: percent of detected faces that are predicted to be female
  - `pct_female_words`: percent of gendered words that are female
  - `pct_female_names`: percent of names that are predicted to be female
  - `pct_mentions_famous_asian`: percent of mentions of famous people that are asian 
  - `pct_mentions_famous_black`: percent of mentions of famous people that are black
  - `pct_mentions_famous_indigeneous`: percent of mentions of famous people that are indigeneous
  - `pct_mentions_famous_latinx`: percent of mentions of famous people that are latinx
  - `pct_mentions_famous_multiracial`: percent of mentions of famous people that are multiracial
  - `pct_mentions_famous_white`: percent of mentions of famous people that are white

## `censored_data/book_purchase_data.Rdata`
This file contains one dataset called `collection_event_time` which contains information on purchases of award winning children's books near the time of award announcement.   
We manually match each award winning children's book in our sample (published between 2016 and 2019) with books purchased in this data by title. 
Then we use purchases of all other books in the children's department that were published between 2016 and 2019 as our comparison group.

We first identify the date each book was eligible for an award (the yearly awards in our sample are are announced near the end of January and only books published the year before are eligible).
Then we count the number of purchases of each book per day, centered around the award announcement date in the year each book was eligible.
We then find the average purchases of books in a collection/citation category per day.

The variables in this dataset and their descriptions are as follows:
  - `collection_citation`: The collection (e.g. Mainstream or Diversity) and the citation (e.g. Award Winners or Award Honors)
  - `event_time`: number of days since award annoucement in the year a book was eligible
  - `quantity_purchased_scaled`: average number of purchases for books in a given collection_citation and in a given event time
  - `moving_average_quantity_purchased_scaled`: 14-day moving average of `quantity_purchased_scaled`
