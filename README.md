# DSCI510_Final

**DATASET 1**

The first section of the notebook: '**Dataset 1: Average Household Income in Los Angeles County by Zipcode**' scrapes the webpage: https://www.point2homes.com/US/Neighborhood/CA/Los-Angeles-County-Demographics.html#MedianIncomeByZipcode.

Run the first cell in this section, the table is scraped, data type updated to numeric for further analysis, and the data is stored in the dataframe df1. The original table is rather small with around 300 rows, and therefore it stops running and return the dataframe within 20 seconds.

I run the second cell to convert the dataframe to csv and save it on my computer with this specific path.

Run the third cell to see the **sample output** of first 5 rows.


**DATASET 2**

Next section in this notebook is '**Dataset 2: Los Angeles County Restaurant Inspection Score**', which includes the first 7000 rows from this online dataset by LA County CIO: https://data.lacounty.gov/datasets/lacounty::public-health-los-angeles-county-restaurant-and-market-inspections-/about.

To retrieve the data from API, run the first cell in this section. '**resultRecordCount=1000**' in the url means it returns 1000 records. Modify this number from 1 to 1000 as you wish to retrieve certain number of records. '**resultOffset={offset}**' means you skip the first 1000 rows. Modify this number to retrieve records after that. 

I set the offset 7 times to get the first 7000 records, update the datatype and store the data in the dataframe df2. This step takes less than 5 seconds.

Similar to dataset 1, I run the second cell to convert the dataframe to csv and save it in the same folder.

Run the third cell to see the **sample output** of first 5 rows.


**DATASET 3**

The final section is '**Dataset 3: Los Angeles County Restaurant Rating and Price**', in which the data is downloaded using Yelp API: https://docs.developer.yelp.com/reference/v3_business_search.

Run the first cell to download the restaurants. In the URL, '**location=CA%20{zc}**' means I search by the zipcode I scraped from Dataset 1, '**sort_by=distance**' to make sure the results are in this zipcode as many as possible, and '**limit=50**' to return 50 restaurants for each zipcode. All the parameters can be changed as needed.

Run the second cell to store all the data in the dataframe df3.

Both the third and fourth cell are to clean df3, as it's not downloaded from a clean table, like dataset 1 and 2. 

What the third dataset do is to first drop any duplicate records, change zipcode to a 5-digit format and then convert the datatype of zipcode to int to achieve consistency. If any error message is returned, simply include this data to the list in 'replace(['', 'B47 5', 'T12 C'], '00000')' then it's good to go.

Run the forth cell to select the rows with zipcode in the Dataset 1 and valid rating and price. Restaurants with rating of 0 and price of 0 are deleted from this dataset because they're not representative. The number of price is the number of dollar signs you see from Yelp, ranging from 1 to 4, meaning from cheap to expensive.

Run the next cell to save the dataframe as csv in my computer.

Run the next cell to see the **sample output** of dataset 3.

The final cell is the option cell as a **sample mode** to test the function of using Yelp API to download data, providing you with 50 restaurants in LA, which should take you no more than 3 seconds.
