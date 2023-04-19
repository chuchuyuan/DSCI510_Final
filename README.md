# DSCI510_Final

**DATASET 1**

The first section of the notebook: '**Dataset 1: Average Household Income in Los Angeles County by Zipcode**' scrapes the webpage: https://www.point2homes.com/US/Neighborhood/CA/Los-Angeles-County-Demographics.html#MedianIncomeByZipcode.

Run the first cell in this section, the table is scraped, data type updated to numeric for further analysis, and the data is stored in the dataframe df1. The original table is rather small with around 300 rows, and therefore it stops running and return the dataframe within 20 seconds.

<img width="916" alt="Screenshot 2023-04-18 at 18 13 33" src="https://user-images.githubusercontent.com/114114911/232941192-f79fdf2b-dd3f-4ec5-869d-7436f4a4d3c4.png">


I run the second cell to convert the dataframe to csv and save it on my computer with this specific path.

<img width="852" alt="Screenshot 2023-04-18 at 18 14 29" src="https://user-images.githubusercontent.com/114114911/233212132-a88aa8e1-2af4-44b1-b92a-411beba97ac6.png">


Run the third cell to see the **sample output** of first 5 rows.

<img width="435" alt="Screenshot 2023-04-19 at 15 19 27" src="https://user-images.githubusercontent.com/114114911/233212195-b52101e9-4f36-44f7-806d-1e7a012d61dd.png">



**DATASET 2**

Next section in this notebook is '**Dataset 2: Los Angeles County Restaurant Inspection Score**', which includes the first 7000 rows from this online dataset by LA County CIO: https://data.lacounty.gov/datasets/lacounty::public-health-los-angeles-county-restaurant-and-market-inspections-/about.

To retrieve the data from API, run the first cell in this section. '**resultRecordCount=1000**' in the url means it returns 1000 records. Modify this number from 1 to 1000 as you wish to retrieve certain number of records. '**resultOffset={offset}**' means you skip the first 1000 rows. Modify this number to retrieve records after that. 

<img width="1313" alt="Screenshot 2023-04-19 at 15 19 54" src="https://user-images.githubusercontent.com/114114911/233212239-7e031ace-1a72-427a-b6f1-57561f0e0b41.png">


I set the offset 7 times to get the first 7000 records, update the datatype and store the data in the dataframe df2. This step takes less than 5 seconds.

Similar to dataset 1, I run the second cell to convert the dataframe to csv and save it in the same folder.

<img width="888" alt="Screenshot 2023-04-19 at 15 20 17" src="https://user-images.githubusercontent.com/114114911/233212289-be801e65-8dd6-4e18-af5e-d45021cbdc3f.png">


Run the third cell to see the **sample output** of first 5 rows.

<img width="478" alt="Screenshot 2023-04-19 at 15 20 29" src="https://user-images.githubusercontent.com/114114911/233212319-0064879b-9a44-469c-9035-04473d3f4288.png">



**DATASET 3**

The final section is '**Dataset 3: Los Angeles County Restaurant Rating and Price**', in which the data is downloaded using Yelp API: https://docs.developer.yelp.com/reference/v3_business_search.

Run the first cell to download the restaurants. In the URL, '**location=CA%20{zc}**' means I search by the zipcode I scraped from Dataset 1, '**sort_by=distance**' to make sure the results are in this zipcode as many as possible, and '**limit=50**' to return 50 restaurants for each zipcode. All the parameters can be changed as needed.

<img width="1220" alt="Screenshot 2023-04-19 at 15 20 45" src="https://user-images.githubusercontent.com/114114911/233212349-25ad9da1-5a3a-4f1f-ab0a-e18afee87061.png">


Run the second cell to store all the data in the dataframe df3.

<img width="846" alt="Screenshot 2023-04-19 at 15 20 58" src="https://user-images.githubusercontent.com/114114911/233212373-16d5a4ca-045a-401a-9414-cfb1d9bfc466.png">


Both the third and fourth cell are to clean df3, as it's not downloaded from a clean table, like dataset 1 and 2. 

What the third dataset do is to first drop any duplicate records, change zipcode to a 5-digit format and then convert the datatype of zipcode to int to achieve consistency. If any error message is returned, simply include this data to the list in 'replace(['', 'B47 5', 'T12 C'], '00000')' then it's good to go.

<img width="598" alt="Screenshot 2023-04-19 at 15 21 16" src="https://user-images.githubusercontent.com/114114911/233212408-867bb4ec-72ef-4848-963e-75d994d76e05.png">


Run the forth cell to select the rows with zipcode in the Dataset 1 and valid rating and price. Restaurants with rating of 0 and price of 0 are deleted from this dataset because they're not representative. The number of price is the number of dollar signs you see from Yelp, ranging from 1 to 4, meaning from cheap to expensive.

<img width="547" alt="Screenshot 2023-04-19 at 15 21 37" src="https://user-images.githubusercontent.com/114114911/233212457-5ab2451c-539b-4372-b610-8e5aa85d94ac.png">


Run the next cell to save the dataframe as csv in my computer.

<img width="904" alt="Screenshot 2023-04-19 at 15 21 50" src="https://user-images.githubusercontent.com/114114911/233212476-c28232b4-5828-4976-bb10-4b304bb4c15f.png">


Run the next cell to see the **sample output** of dataset 3.

<img width="480" alt="Screenshot 2023-04-19 at 15 22 02" src="https://user-images.githubusercontent.com/114114911/233212503-f0568e06-714d-499b-bd96-9b85e7b1b4a5.png">

The final cell is the option cell as a **sample mode** to test the function of using Yelp API to download data, providing you with 50 restaurants in LA, which should take you no more than 3 seconds.

<img width="1241" alt="Screenshot 2023-04-19 at 15 29 46" src="https://user-images.githubusercontent.com/114114911/233213679-fc267ff7-fdc0-4041-892f-abb918f4c159.png">
