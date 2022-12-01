# FlightRadar24

## Context
A data engineer often have to create and process ETL jobs and data pipelines.
For this project you'll have to ``extract`` data from https://www.flightradar24.com/ (a track of all flights world-wide, an airport and company listing).

After extracting the data you'll have to ``transform`` it (e.g pyspark, pandas, ...) to finaly implement answers to our questions.

Please commit early & often :)

## Accessing FlightRadar24 made easy in Python
The FlightRadarAPI project is available for you to simplify you queries to the FlightRadar24 API : https://github.com/JeanExtreme002/FlightRadarAPI 

## Questions

    - Q1: What is the company with the most active flights in the world ?
    - Q2: By continent, what are the companies with the most regional active flights (airports of Origin & Destination within the same continent) ?
    - Q3: World-wide, Which active flight has the longest route ?
    - Q4: By continent, what is the average route distance ? (flight localization by airport of origin)
    - Q5.1: Which leading airplane manufacturer has the most active flights in the world ?
    - Q5.2: By continent, what is the most frequent airplane model ? (airplane localization by airport of origin)
    - Q6: By company registration country, what are the tops 3 airplanes model flying ?
    - Q7.1: By continent, what airport is the most popular destination ?
    - Q7.2: What airport airport has the greatest inbound/outbound flights difference ? (positive or negative)
    - Q8: By continent, what is the average active flight speed ? (flight localization by airport of origin)

## Evaluation criteria
 * We love ``Craftsmanship, clean code``.
 * Spark implementation appreciated.
 * Generation, storage, ingestion, transformation, serving data.
 * Keep in mind that you code will run on production environment (so must be industrialized) in purpose to be analyse by a Data Scientist/Data Analyst.
