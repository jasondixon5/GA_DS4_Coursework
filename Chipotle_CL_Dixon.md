# Chipotle Command Line Homework

##Command Line Tasks

###Look at the head and the tail of chipotle.tsv in the data subdirectory of this repo. Think for a minute about how the data is structured. What do you think each column means? What do you think each row means? Tell me! (If you're unsure, look at more of the file contents.)

`cd /Users/jasondixon/GA_DS_Class/GH_DS_SEA_4/DS-SEA-4/data`

`head chipotle.tsv`

The file appears to be a list of items ordered from Chipotle. Each row is an item; each item is associated with an order idea, so there appear to be multiple items per order ID. Each item has the following info available: the order ID of the associated order, the quantity of that item ordered on that order, the item name, a description indicating the options the customer selected (or a generic description like apple), and the price per unit of the item.

###How many orders do there appear to be?

`sort -g chipotle.tsv | cut -f1 | uniq -c | wc -l`

Output:

`1835`

There are 1,835 unique lines in the file; this means there are 1,834 unique orders plus a header row.

###How many lines are in this file?

`wc chipotle.tsv`

Output:

`4623   55837  364975 chipotle.tsv`

`wc -l chipotle.tsv`

Output:

`4623 chipotle.tsv`

There are 4,623 lines in the file, so there are 4,622 data rows plus one header row.

###Which burrito is more popular, steak or chicken?

`cut -f3 chipotle.tsv | sort | uniq -c`

Partial Output:

` 726 Chicken Bowl
 553 Chicken Burrito
  47 Chicken Crispy Tacos `
 
 `101 Side of Chips
 211 Steak Bowl
 368 Steak Burrito `
 
 Chicken burritos are more popular than steak burritos.

###Do chicken burritos more often have black beans or pinto beans?

`grep "Chicken Burrito" chipotle.tsv | grep "Black Beans" | wc -l`

`grep "Chicken Burrito" chipotle.tsv | grep "Pinto Beans" | wc -l`

There are 282 chicken burritos ordered with black beans and only 105 chicken burritos ordered with pinto beans, so black beans were ordered more often. Caution: These numbers will double count those orders with BOTH black beans and pinto beans, so additional research would need to be done to calculate separate counts of burritos with only one or the other.


###Make a list of all of the CSV or TSV files in the our class repo. repo (using a single command). You will be working on your local repo on your laptop. Think about how wildcard characters can help you with this task.

`Jasons-MacBook-Air:GH_DS_SEA_4 jasondixon$ find . -name "*.csv"`

Output:
`
./DS-SEA-4/data/Airline_on_time_west_coast.csv
./DS-SEA-4/data/airlines.csv
./DS-SEA-4/data/bank-additional.csv
./DS-SEA-4/data/bikeshare.csv
./DS-SEA-4/data/citibike_feb2014.csv
./DS-SEA-4/data/drinks.csv
./DS-SEA-4/data/drones.csv
./DS-SEA-4/data/hitters.csv
./DS-SEA-4/data/icecream.csv
./DS-SEA-4/data/imdb_1000.csv
./DS-SEA-4/data/mtcars.csv
./DS-SEA-4/data/NBA_players_2015.csv
./DS-SEA-4/data/ozone.csv
./DS-SEA-4/data/pronto_cycle_share/2015_station_data.csv
./DS-SEA-4/data/pronto_cycle_share/2015_trip_data.csv
./DS-SEA-4/data/pronto_cycle_share/2015_weather_data.csv
./DS-SEA-4/data/rossmann.csv
./DS-SEA-4/data/rt_critics.csv
./DS-SEA-4/data/stores.csv
./DS-SEA-4/data/syria.csv
./DS-SEA-4/data/time_series_train.csv
./DS-SEA-4/data/titanic.csv
./DS-SEA-4/data/ufo.csv
./DS-SEA-4/data/vehicles_test.csv
./DS-SEA-4/data/vehicles_train.csv
./DS-SEA-4/data/yelp.csv
`

`Jasons-MacBook-Air:GH_DS_SEA_4 jasondixon$ find . -name "*.tsv"`

Output:
`
./DS-SEA-4/data/chipotle.tsv
./DS-SEA-4/data/sms.tsv
`
###Count the approximate number of occurrences of the word "dictionary" (regardless of case) across all files of our class repo.
`grep -ri "dictionary" . | wc -l`

Output:

`79`

###Optional: Use the the command line to discover something "interesting" about the Chipotle data. Try using the commands from the "advanced" section!
What is the most expensive line item on any order in the list?

`cut -f1,2,3,5 chipotle.tsv | sort -n -t$ -k2`

Partial Output: 

`511	3	Steak Burrito	$27.75 
178	3	Chicken Bowl	$32.94 
1443	3	Veggie Burrito	$33.75 
1443	4	Chicken Burrito	$35.00 
511	4	Chicken Burrito	$35.00 
1398	3	Carnitas Bowl	$35.25 
1443	15	Chips and Fresh Tomato Salsa	$44.25`

The most expensive line item was a 15 orders of chips and salsa on order # 1443 (totaling $44.25).


