# DataScienceBlogPost
Udacity - Data Science Blog Post - Project

# Project Introduction:

from project requirements
The project is to select any publically available data set, understand the data and the domain, then answer 3-6 different question related to the data set.   
I choose airbnb - Boston dataset, which is available on Kaggle, which AirBnB has made public of its rental properties in and around Boston, MA neighborhoods, along with the reviews left by the guests and the dates when properties were available. In this blog we review this data to learn about the neighborhood and attempts to understand what types of properties are available, their prices, concentration of these listing, number of reviews and lastly how guests described the properties after their stay.

# Libraries used  
matplotlib - to plot the visuals    
seaborn (v 0.11.2) - to plot the visuals   
pandas 0.23.3  - for data manipulation   
numpy 1.19.5  - for data manipulation  
sklearn 0.24.2,  - for text processing  
python 3.6.3  -  developing language  
nltk  - Text processing  
wordcloud  - presenting the influential words as a visual of words cloud   

# Datasets
Data sets are copied in the data folder. Unzip and copy these in the data folder. The notebook was created in kaggle and has kaggle specific file location

## Property listing:   
Contains the detail about the property, captured under 95 different attributes. It describes property in terms of its location, availability, price, amenities, details about host and many others. Here is complete list of attributes (columns) available in the listing data

<class 'pandas.core.frame.DataFrame'>  
RangeIndex: 3585 entries, 0 to 3584  
Data columns (total 95 columns):  
|  #. | Column                           | Non-Null Count | Dtype | 
|-----|----------------------------------|----------------| ----- |     
| 0   |id                                |3585 non-null   |int64 | |  
| 1   |listing_url                       |3585 non-null   |object |   
| 2   |scrape_id                         |3585 non-null   |int64 |  |   
| 3   |last_scraped                      |3585 non-null   |object |  
| 4   |name                              |3585 non-null   |object |   
| 5   |summary                           |3442 non-null   |object |  
| 6   |space                             |2528 non-null   |object |  
| 7   |description                       |3585 non-null   |object |  
| 8   |experiences_offered               |3585 non-null   |object |  
| 9   |neighborhood_overview             |2170 non-null   |object |  
| 10  |notes                             |1610 non-null   |object |  
| 11  |transit                           |2295 non-null   |object |  
| 12  |access                            |2096 non-null   |object |  
| 13  |interaction                       |2031 non-null   |object |  
| 14  |house_rules                       |2393 non-null   |object |  
| 15  |thumbnail_url                     |2986 non-null   |object |  
| 16  |medium_url                        |2986 non-null   |object |  
| 17  |picture_url                       |3585 non-null   |object |  
| 18  |xl_picture_url                    |2986 non-null   |object |  
| 19  |host_id                           |3585 non-null   |int64 |   
| 20  |host_url                          |3585 non-null   |object |  
| 21  |host_name                         |3585 non-null   |object |  
| 22  |host_since                        |3585 non-null   |object |  
| 23  |host_location                     |3574 non-null   |object |  
| 24  |host_about                        |2276 non-null   |object |  
| 25  |host_response_time                |3114 non-null   |object |  
| 26  |host_response_rate                |3114 non-null   |object |  
| 27  |host_acceptance_rate              |3114 non-null   |object |  
| 28  |host_is_superhost                 |3585 non-null   |object |  
| 29  |host_thumbnail_url                |3585 non-null   |object |  
| 30  |host_picture_url                  |3585 non-null   |object |  
| 31  |host_neighbourhood                |3246 non-null   |object |  
| 32  |host_listings_count               |3585 non-null   |int64 |   
| 33  |host_total_listings_count         |3585 non-null   |int64 |   
| 34  |host_verifications                |3585 non-null   |object |  
| 35  |host_has_profile_pic              |3585 non-null   |object |  
| 36  |host_identity_verified            |3585 non-null   |object |  
| 37  |street                            |3585 non-null   |object |  
| 38  |neighbourhood                     |3042 non-null   |object |  
| 39  |neighbourhood_cleansed            |3585 non-null   |object |  
| 40  |neighbourhood_group_cleansed      |0 non-null      |float64 |  
| 41  |city                              |3583 non-null   |object |  
| 42  |state                             |3585 non-null   |object |  
| 43  |zipcode                           |3547 non-null   |object |  
| 44  |market                            |3571 non-null   |object |  
| 45  |smart_location                    |3585 non-null   |object |  
| 46  |country_code                      |3585 non-null   |object |  
| 47  |country                           |3585 non-null   |object |  
| 48  |latitude                          |3585 non-null   |float64 |  
| 49  |longitude                         |3585 non-null   |float64 |  
| 50  |is_location_exact                 |3585 non-null   |object |  
| 51  |property_type                     |3582 non-null   |object |  
| 52  |room_type                         |3585 non-null   |object |  
| 53  |accommodates                      |3585 non-null   |int64 |   
| 54  |bathrooms                         |3571 non-null   |float64 |  
| 55  |bedrooms                          |3575 non-null   |float64 |  
| 56  |beds                              |3576 non-null   |float64 |  
| 57  |bed_type                          |3585 non-null   |object |  
| 58  |amenities                         |3585 non-null   |object |  
| 59  |square_feet                       |56 non-null     |float64 |  
| 60  |price                             |3585 non-null   |object |  
| 61  |weekly_price                      |892 non-null    |object |  
| 62  |monthly_price                     |888 non-null    |object |  
| 63  |security_deposit                  |1342 non-null   |object |  
| 64  |cleaning_fee                      |2478 non-null   |object |  
| 65  |guests_included                   |3585 non-null   |int64 |   
| 66  |extra_people                      |3585 non-null   |object |  
| 67  |minimum_nights                    |3585 non-null   |int64 |   
| 68  |maximum_nights                    |3585 non-null   |int64 |   
| 69  |calendar_updated                  |3585 non-null   |object |  
| 70  |has_availability                  |0 non-null      |float64 |  
| 71  |availability_30                   |3585 non-null   |int64 |   
| 72  |availability_60                   |3585 non-null   |int64 |   
| 73  |availability_90                   |3585 non-null   |int64 |   
| 74  |availability_365                  |3585 non-null   |int64 |   
| 75  |calendar_last_scraped             |3585 non-null   |object |  
| 76  |number_of_reviews                 |3585 non-null   |int64 |   
| 77  |first_review                      |2829 non-null   |object |  
| 78  |last_review                       |2829 non-null   |object |  
| 79  |review_scores_rating              |2772 non-null   |float64 |  
| 80  |review_scores_accuracy            |2762 non-null   |float64 |  
| 81  |review_scores_cleanliness         |2767 non-null   |float64 |  
| 82  |review_scores_checkin             |2765 non-null   |float64 |  
| 83  |review_scores_communication       |2767 non-null   |float64 |  
| 84  |review_scores_location            |2763 non-null   |float64 |  
| 85  |review_scores_value               |2764 non-null   |float64 |  
| 86  |requires_license                  |3585 non-null   |object |  
| 87  |license                           |0 non-null      |float64 |  
| 88  |jurisdiction_names                |0 non-null      |float64 |  
| 89  |instant_bookable                  |3585 non-null   |object |  
| 90  |cancellation_policy               |3585 non-null   |object |  
| 91  |require_guest_profile_picture     |3585 non-null   |object |  
| 92  |require_guest_phone_verification  |3585 non-null   |object |  
| 93  |calculated_host_listings_count    |3585 non-null   |int64 |   
| 94  |reviews_per_month                 |2829 non-null   |float64 |  

dtypes: float64(18), int64(15), object(62)  
memory usage: 2.6+ MB  

## Reviews :   
It contains the reviewer name, property id, date of review and comments, expressing their experience during their stay.  

<class 'pandas.core.frame.DataFrame'>  
RangeIndex: 68275 entries, 0 to 68274  
Data columns (total 6 columns):  

|  #. | Column        | Non-Null Count | Dtype |  
|-----|---------------|----------------| ----- |      
| 0   |listing_id     |68275 non-null  |int64  |   
| 1   |id             |68275 non-null  |int64  |  
| 2   |date           |68275 non-null  |object |  
| 3   |reviewer_id    |68275 non-null  |int64  |  
| 4   |reviewer_name  |68275 non-null  |object |  
| 5   |comments       |68222 non-null  |object |  
  
dtypes: int64(3), object(3)  
memory usage: 3.1+ MB  


## Calendar:  
It contains the dates when each of the properties in this data set are available or not available for rent.  

<class 'pandas.core.frame.DataFrame'>   
RangeIndex: 1308890 entries, 0 to 1308889   
Data columns (total 5 columns):  

|  #. | Column        | Non-Null Count | Dtype |  
|-----|---------------|----------------| ----- |        
| 0   |listing_id  |1308890 non-null  |int64 |    
| 1   |date        |1308890 non-null  |object |  
| 2   |available   |1308890 non-null  |object |  
| 3   |price       |643037 non-null   |object |  
| 4   |price_num   |643037 non-null   |float64|  

dtypes: float64(1), int64(1), object(3)  
memory usage: 49.9+ MB  


# Conclusion  
Apartments are the most common property type, with over 70% of all rental property types. Over 60% of listings have offered the entire home or apartment for rent. Interestingly, we also find boats, dorms, villas, and camper/RV’s listed as rental properties. We also find that the downtown or urban areas have overwhelmingly more apartment listings in comparison to suburbs where homeowners rented out private rooms.  

Half of the neighborhoods have listed over 80% of the available rental properties on Airbnb. Apart from some oddly low rental prices of $15 and some as large as $4,000, most remained closely comparable to each other.  

The vast majority of reviewers stayed at one property. There is a small number that stayed at more than three properties.  

Most of the reviews are positive, although we don’t these classified as positive or negative. However, the words used by guests to express their feelings regarding their stay were overwhelmingly positive.  

# Acknowledgements  
https://udacity.com : Extra curricular - Data Visualization, apart from the classroom material  
https://scikit-learn.org  : for text processing reference  
https://pandas.pydata.org/ : for data processing reference   
https://seaborn.pydata.org/ : for visuals and parameters reference  
https://matplotlib.org/  : for visuals and parameters reference  
https://numpy.org/ : for reference  
www.stackoverflow.com : Used to resolve the coding issues  
www.statology.org  : to understanding some concepts  
https://www.nltk.org/howto/tokenize.html : Text Processing reference  
https://pythonexamples.org/nltk-pos-tagging/ : POS tagging reference   
https://medium.com : for articles to develop/clear concept/understanding of the topic  
https://towardsdatascience.com : for articles to develop/clear understanding of the topic 




