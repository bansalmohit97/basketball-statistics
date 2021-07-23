# basketball-statistics

Overview: Dataset -> TETLT -> Visualisation

Tools Used: Microsoft Excel, Microsoft Visual Studio Shell (SSIS), Microsoft SQL Server, Tableau

The dataset for this project was taken from Kaggle. The data describes the statistics of the basketball players across various seasons (1999 - 2020). 

It is known that the real world datasets are not at all tidy, they are mostly (99.99% of the time) uncleaned, and as a Data Scientist, the total time that you assign to a project, over 70% of it is consumed during the ETL process (Extraction, Transformation & Loading), which I believe is the key and the prime step towards the commencement of any DS project. This was the case here as well, therefore I followed a blueprint which provided me room for the least number of errors possible and the maximum efficiency (follow the project attached above). The process I followed was TETLT (Transform, Extract, Transform, Load, Transform). First, the csv file had to be converted to .txt file and I opened it in Microsoft Excel using Text Query Editor where the first transformation was performed. The first QA check was to find out the columns like DOB and Currency related in the dataset, whose datatypes were changed from text to date, currency (without $ and separator). Save the file in '.csv' format. 

This was followed by opening the file in Microsoft Visual Studio and creating a control flow and a data flow. Within a data flow, the .csv file was opened in the Source container (Flat File Source in this case) along with some changes made to the maximum limit of input cell characters corresponding each column. (Extraction)
The Transformation that was performed following this was carried out using a Conditional Split which removed all the bad records from the dataset (there were some cells in the birth_year which had misleading entries, 318 rows to be precise). 
Segregating the 'not-so-good' data, the rows that were left (mind it the data type of all columns excluding a few is still 'Text') were uploaded into the OLE DB Destination which represents the database that was created in the MS-SQL Server. (Loading)

The table that was published in the database is still RAW and has to be converted into a WORKING table using a BUILD process which was carried out using Stored Procedures (just to make sure that the file remains saved for the future use and we do not want it to be saved in the local directory). A complete script was written in SQL (again in a manner that is more understandable and easier to use and involves the least errors). This is the time when the last Transformation was carried out since, the conversion showed some errors (including the truncation error and data type conversion error) and this time the transformation was done using SQL Queries.

Once the file was uploaded successfully, I connected Tableau to the Server and created various hypothesis and manual questions (to start with), followed by coming up with metrics to judge and arrange the players on (Performance Efficiency Rate and Three Pointer Accuracy in this case), the reasons for choosing this is enclosed in the 'Insights' Folder attached. Various vizzes were created an then combined to come up with a proper dashboard (.twb is in the 'Visualisations' Folder and it is also uploaded on Tableau Public whose link is provided below)

https://public.tableau.com/views/BasketballPlayersStatisticsbySeason1999-2020/PlayersStatsbySeason?:language=en-US&:display_count=n&:origin=viz_share_link

