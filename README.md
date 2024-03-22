# Netflix Dashboard

### Dashboard Link : https://www.novypro.com/profile_projects/ayan-malik

## About Netflix :

Netflix is the world's leading internet entertainment Content (TV series,documentaries and feature films) across a wide variety of genres and languages.
Subscribers can watch as much as they want, anytime, anywhere, on any internet-connected screen.
Members can play, pause and resume watching, all without commercials or commitments.

#Netflix Dashboard: 

Netflix Dashboard allows end user to Analyse different aspacts and Insights about Netflix Content. 
blow are some Important Analysis -


* Total Number of TV Shows
* Total Number of Movies
* Total Number of Genres
* Total Number of Votes
* Top 10 Movies Running by its IMDB Ratings.
* Titles by Realsed Year and Type.
* Different Genres and Categorys


Through Above Analysis End user can have a Comprehensive Idea about Netflix Running Content.




### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present in Dataset.
- Step 5 : Since dataset is not strctured in Proper way so Aplied steps Like Promoted Headers, Added and Removed Columns, Renamed Columns, Added Conditional Columns
 	   and Column From Examle etc.
- Step 6 : Calender table wasn't Requried, Didn't try to increase Model Size by Genrating Calender Table.
- Step 7 : Since the dataset contains only Two Tables, thus in order to Create relationships, Create one to many Relationship Between Titles and Creadit Table.
And Filter Cardinality was Single Directional.

# Snapshot of Data Model and Relationship.          

![Scheama](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/aedb4d61-9c26-43e2-9565-ce5bbf0b53b4)

![Cardinality](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/21b55c6f-f257-4bbf-99bf-3b79b3093083)


- Step 8 : In the report view, under the view tab, Set the canvas Color as Dark Black.

*** Visuals And Tabs***
### Content Summary --

- Step 9 : Added 4 Card Visual to show Total TV Shows, Total Movies, Count Of Genres and Total Voting Score.

![Card 1](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/233899eb-0b7b-4c9a-b7a3-29bfb8716494)


![Card 2](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/7d435e3a-8ffb-488d-bc08-86ec61b6de0b)


- Step 10: Added Donut chart Visual to showcase Total Content along with Two Magor Category Tv Shows and Movies.

![Donut Netflix](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/3199d54a-4110-4295-9e9c-5e43c7da93af)

- Step 11: Added Pie Chart Visual to Showcase Different Gernes About Content, Comedy, Horror, Romantic etc.

![Pie](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/2b6c7e8a-bf87-4d11-b717-10b3e9ca6390)



- Step 12: Added Clustered Bar chart Visual to show Top 10 Movies by IMDB Ratings and Votes.


![Top 10 Movies](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/1a4f9056-7ea1-4f8b-8369-a8f14faa821a)



- Step 13: Visual filters (Slicers) were added as a Released Year Filter, User can Salect Desire Year.

![Filter](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/668785a6-b47b-42cf-988f-59b09c06a135)



- Step 14: Area Chart Visual was added to showcase Released Titles by Year and Type.

![Area](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/a88ea41a-ec51-42a4-b377-74867c6d831d)


## Didn't use any calculated Column so that Model size should not be Increase.

## New Measure Table was added to Data Model.
        
- Step 15 : New measure was created to calculate To Total Action Movies

Following DAX expression was written for the same,
        
    Total Action = 
        CALCULATE(
            COUNT(
                Credits[Tittle ID]
            ),
            Titles[Genres.1]= "Action"
        )

A Pie chart visual was used to represent Total Action Movies.

![Pie](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/2b6c7e8a-bf87-4d11-b717-10b3e9ca6390)

        
 - Step 16 : New measure was created to calculate To Total Comedy Movies.


                Total Comedy = 
                        CALCULATE(
                            COUNT(
                                 Credits[Tittle ID]
                                ),

                            Titles[Genres.1]= "Comedy"
                            
                        )
 
Same Pie chart visual was used to represent Total Action Movies.
 
- Step 17 : New measure was created to calculate To Total Crime Movies

Following DAX expression was written for the same,

      Total Crime = 
            CALCULATE(
                COUNT(
                     Credits[Tittle ID]
                    ),
                    Titles[Genres.1]= "Crime"
                )

Same Pie chart visual was used to represent Total Action Movies.
 
 

 
- Step 18 : New measure was created to calculate To Total Horror Movies

Following DAX expression was written for the same,


        Total Horror = 
                CALCULATE(
                    COUNT(
                        Credits[Tittle ID]
                    ),
                    Titles[Genres.1]= "Horror"
                )

Same Pie chart visual was used to represent Total Action Movies.

- Step 19 : New measure was created to calculate To Total Romance Movies

Following DAX expression was written for the same,


            Total Romance = 
                    CALCULATE(
                            COUNT(
                                Credits[Tittle ID]
                            ),
                        Titles[Genres.1]= "Romance"
                    )

Same Pie chart visual was used to represent Total Action Movies.


- Step 20 : New Table was created to Data Model to calculate Top 10 Movies.

Following DAX expression was written for the same,


		    Top 10 Movie = 
                    TOPN(
                        10,
                        SUMMARIZE(
                                 Titles,
                                Titles[Tittle],Titles[IMDB Score],
                                "Top Ratings",
                                [Sum Of IMDB Score]
                            ),
                        [Sum Of IMDB Score],
                         DESC
                     )

![Top 10 Movies Table](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/0be69467-b955-4e9a-9c7d-1aa9886110f2)

A Cluster Bar chart visual was used to represent Top 10 Movies By Ratings.

![Top 10 Movies](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/1a4f9056-7ea1-4f8b-8369-a8f14faa821a)




- Step 21 : Netflix Logo Was interted.


 - Step 22 : The report was then published to Power BI Service.

 # Snapshot of Dashboard (Power BI Service)

![Netflix BI Service](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/85abc94a-b481-4a91-b36b-6eec0cc8bee2)
 
# Report Snapshot (Power BI DESKTOP)

![Netflix BI Desktop](https://github.com/ayanmalik/Netflix-Dashboard/assets/15996271/313795d1-f1e4-4060-8606-cbf33bd2fbb0)



A Single page report was created on Power BI Desktop & it was then published to Power BI Service.


 


