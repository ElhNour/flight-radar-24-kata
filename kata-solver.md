# Flight Radar 24 Kata

This repository contains a pipeline for extracting, transforming, and loading data from the FlightRadar24 API. The pipeline processes data related to global flights, airports, and airline companies.

## Overview

The pipeline is designed to provide the following key indicators:

- The airline company with the highest number of ongoing flights.
- For each continent, the airline company with the highest number of active regional flights.
- The ongoing flight with the longest route.
- For each continent, the average flight time duration.
- The aircraft model with the highest number of active flights.
- For each airline's country, the top 3 aircraft models in use.

The pipeline is run periodically (we can specify the time period in seconds, minutes or hours), and logs the results using a csv format.

## Requirements

- Python 3.x
- Apache Spark
- apscheduler
- FlightRadarAPI library (https://github.com/JeanExtreme002/FlightRadarAPI)

## Installation

1. Clone this repository:

   ```shell
   git clone https://github.com/ElhNour/flight-radar-kata.git
   ```

2. Install the required dependencies.


## Usage

1. Run the ETL pipeline by running all notebook cells.

   This will trigger the extraction, transformation, and loading of data from the FlightRadar24 API.

2. Monitor the pipeline execution logs for information and progress updates.

3. Access the stored data in the designated storage mechanism to retrieve the desired values.

## Design choices
1. Define a function for each indicator for modularity.
2. Define a global function that runs the ETL periodically (apscheduler module offers this feature).
3. Use pyspark.sql dataframe as mentioned in the instructions, clean the data.
4. For the first task, we first filter active flights to optimize complexity, then group by airline icao and count the number of corresponding flights. We apply the maximum to the count to obtain the result.
5. For the second task, we first filter the active regional flights, create a new column indicating the continent through which the flight is currently transiting. We group the flights by continent and airline icao, and count the number of flights for each pair. Since our aim is to find the most active airline by continent, we partition the resulting dataframe by continent and rank it in descending order (by number of flights). We assign each line its own number in the partition, and keep only line 1, which represents the result.
6. The third task is to sort the flights by time in descending order, keeping only the first line representing the longest trip.
7. In the fourth task, we group the flights by continent, then calculate the average of the time column to obtain the average per continent.
8. In the fifth task, we filter the active flights, form aircraft code groups, count the number of flights, order the count in descending order and keep only the first.
9. The sixth task is to group the flights according to airline iata and aircraft code, count the number of corresponding flights and order them in descending order. Next, the dataframe is partitioned by airline iata and a 'row number' column is added to retain only the first three elements, representing the top three aircraft models used by the airline.