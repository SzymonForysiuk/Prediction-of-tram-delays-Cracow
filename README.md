## Prediction of tram delays in Cracow

The project is related to an individual competition held by Dataworkshop’s Data Science
Club, in which I actively participated as an individual contestant. The main aim of this project was to
develop a precise predictive model that can forecast tram delays in the city of Kraków. This was
achieved by developing a machine learning model or neural network that can accurately predict
delays, measured in seconds.
Trams are an essential mode of public transportation in Krakow. Accurately predicting tram
delays can improve the quality of service provided to commuters. The data contains the following
columns: id, delay (dependent variable), datetime, stop, stop_name, number, direction,
planned_time, vehicle_id, trip_id, seq_num. 

Variables:
  
1. id - id of a record in the data
1. delay 
1. stop - id of the tram stop
1. stop_name - the name of the tram stop
1. number - number of the tram line
1. planned_time - planned time at which the tram was supposed to arrive at a given stop
1. vehicle_id - id of the machine/tram
1. trip_id - trip id
1. seq_num - number of the stop in the tram route

Example of one streetcar route. Line number 44, which goes from Kopiec Wandy to Bronowice.
  
|     id |   delay |   stop | stop_name                     |   number | direction   | planned_time        |   vehicle_id |             trip_id |   seq_num |
|-------:|--------:|-------:|:------------------------------|---------:|:------------|:--------------------|-------------:|--------------------:|----------:|
| 120757 |       0 |    450 | Kopiec Wandy                  |       44 | Bronowice   | 2018-07-25 15:58:00 |  6.35219e+18 | 6351558574044977929 |         1 |
| 121014 |     102 |    459 | Kombinat                      |       44 | Bronowice   | 2018-07-25 16:01:00 |  6.35219e+18 | 6351558574044977929 |         2 |
| 121235 |      65 |    423 | Struga                        |       44 | Bronowice   | 2018-07-25 16:07:00 |  6.35219e+18 | 6351558574044977929 |         3 |
| 121415 |      67 |   2744 | Plac Centralny im. R.Reagana  |       44 | Bronowice   | 2018-07-25 16:11:00 |  6.35219e+18 | 6351558574044977929 |         4 |
| 121475 |      83 |    413 | Os.Kolorowe                   |       44 | Bronowice   | 2018-07-25 16:12:00 |  6.35219e+18 | 6351558574044977929 |         5 |
| 121606 |      21 |    408 | Rondo Czyżyńskie              |       44 | Bronowice   | 2018-07-25 16:16:00 |  6.35219e+18 | 6351558574044977929 |         6 |
| 121711 |      29 |    112 | Stella-Sawickiego             |       44 | Bronowice   | 2018-07-25 16:18:00 |  6.35219e+18 | 6351558574044977929 |         8 |
| 121815 |      73 |   2811 | Muzeum Lotnictwa              |       44 | Bronowice   | 2018-07-25 16:20:00 |  6.35219e+18 | 6351558574044977929 |        10 |
| 121889 |       0 |   3040 | TAURON Arena Kraków Wieczysta |       44 | Bronowice   | 2018-07-25 16:23:00 |  6.35219e+18 | 6351558574044977929 |        11 |
| 121946 |       9 |    130 | Białucha                      |       44 | Bronowice   | 2018-07-25 16:24:00 |  6.35219e+18 | 6351558574044977929 |        12 |
| 122017 |       0 |    129 | Cystersów                     |       44 | Bronowice   | 2018-07-25 16:26:00 |  6.35219e+18 | 6351558574044977929 |        13 |
| 122203 |      16 |    126 | Lubicz                        |       44 | Bronowice   | 2018-07-25 16:30:00 |  6.35219e+18 | 6351558574044977929 |        15 |
| 122320 |      58 |    131 | Dworzec Główny                |       44 | Bronowice   | 2018-07-25 16:32:00 |  6.35219e+18 | 6351558574044977929 |        16 |
| 122389 |      42 |   3032 | Stary Kleparz                 |       44 | Bronowice   | 2018-07-25 16:34:00 |  6.35219e+18 | 6351558574044977929 |        17 |
| 122661 |      34 |     79 | Plac Inwalidów                |       44 | Bronowice   | 2018-07-25 16:40:00 |  6.35219e+18 | 6351558574044977929 |        20 |
| 122745 |      40 |     83 | Urzędnicza                    |       44 | Bronowice   | 2018-07-25 16:42:00 |  6.35219e+18 | 6351558574044977929 |        21 |
| 122811 |      14 |     84 | Biprostal                     |       44 | Bronowice   | 2018-07-25 16:44:00 |  6.35219e+18 | 6351558574044977929 |        22 |
| 122866 |      34 |     88 | Uniwersytet Pedagogiczny      |       44 | Bronowice   | 2018-07-25 16:45:00 |  6.35219e+18 | 6351558574044977929 |        23 |
| 122949 |      20 |   1049 | Głowackiego                   |       44 | Bronowice   | 2018-07-25 16:47:00 |  6.35219e+18 | 6351558574044977929 |        24 |
<p><img src="https://plikimpi.krakow.pl//zalacznik/242464/4.jpg" alt="polish sign language"></p>
