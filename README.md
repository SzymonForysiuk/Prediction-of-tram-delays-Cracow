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
  
|     id |   delay |   stop |   number |   vehicle_id |             trip_id |   seq_num |   minute |   hour |   day |   month |   rush_hours |   night_hours | is_weekend   |   time_diff | high_seq_num   |   direction_Bronowice |   direction_Bronowice Małe |   direction_Cichy Kącik |   direction_Cm. Rakowicki |   direction_Czerwone Maki P+R |   direction_Dworzec Tow. |   direction_Kombinat |   direction_Kopiec Wandy |   direction_Krowodrza Górka |   direction_Kurdwanów P+R |   direction_Mały Płaszów |   direction_Mistrzejowice |   direction_Nowy Bieżanów P+R |   direction_Os.Piastów |   direction_Prokocim |   direction_Salwator |   direction_Walcownia |   direction_Wzgórza K. |   direction_Łagiewniki |
|-------:|--------:|-------:|---------:|-------------:|--------------------:|----------:|---------:|-------:|------:|--------:|-------------:|--------------:|:-------------|------------:|:---------------|----------------------:|---------------------------:|------------------------:|--------------------------:|------------------------------:|-------------------------:|---------------------:|-------------------------:|----------------------------:|--------------------------:|-------------------------:|--------------------------:|------------------------------:|-----------------------:|---------------------:|---------------------:|----------------------:|-----------------------:|-----------------------:|
| 120757 |       0 |    450 |       44 |  6.35219e+18 | 6351558574044977929 |         1 |       58 |     15 |     2 |       7 |            1 |             0 | False        |          60 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121014 |     102 |    459 |       44 |  6.35219e+18 | 6351558574044977929 |         2 |        1 |     16 |     2 |       7 |            1 |             0 | False        |           0 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121235 |      65 |    423 |       44 |  6.35219e+18 | 6351558574044977929 |         3 |        7 |     16 |     2 |       7 |            1 |             0 | False        |           0 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121415 |      67 |   2744 |       44 |  6.35219e+18 | 6351558574044977929 |         4 |       11 |     16 |     2 |       7 |            1 |             0 | False        |         120 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121475 |      83 |    413 |       44 |  6.35219e+18 | 6351558574044977929 |         5 |       12 |     16 |     2 |       7 |            1 |             0 | False        |         -60 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121606 |      21 |    408 |       44 |  6.35219e+18 | 6351558574044977929 |         6 |       16 |     16 |     2 |       7 |            1 |             0 | False        |         180 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121711 |      29 |    112 |       44 |  6.35219e+18 | 6351558574044977929 |         8 |       18 |     16 |     2 |       7 |            1 |             0 | False        |          60 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121815 |      73 |   2811 |       44 |  6.35219e+18 | 6351558574044977929 |        10 |       20 |     16 |     2 |       7 |            1 |             0 | False        |         240 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121889 |       0 |   3040 |       44 |  6.35219e+18 | 6351558574044977929 |        11 |       23 |     16 |     2 |       7 |            1 |             0 | False        |         300 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 121946 |       9 |    130 |       44 |  6.35219e+18 | 6351558574044977929 |        12 |       24 |     16 |     2 |       7 |            1 |             0 | False        |         180 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122017 |       0 |    129 |       44 |  6.35219e+18 | 6351558574044977929 |        13 |       26 |     16 |     2 |       7 |            1 |             0 | False        |         120 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122203 |      16 |    126 |       44 |  6.35219e+18 | 6351558574044977929 |        15 |       30 |     16 |     2 |       7 |            1 |             0 | False        |         120 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122320 |      58 |    131 |       44 |  6.35219e+18 | 6351558574044977929 |        16 |       32 |     16 |     2 |       7 |            1 |             0 | False        |          60 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122389 |      42 |   3032 |       44 |  6.35219e+18 | 6351558574044977929 |        17 |       34 |     16 |     2 |       7 |            1 |             0 | False        |          60 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122661 |      34 |     79 |       44 |  6.35219e+18 | 6351558574044977929 |        20 |       40 |     16 |     2 |       7 |            1 |             0 | False        |         120 | False          |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122745 |      40 |     83 |       44 |  6.35219e+18 | 6351558574044977929 |        21 |       42 |     16 |     2 |       7 |            1 |             0 | False        |         300 | True           |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122811 |      14 |     84 |       44 |  6.35219e+18 | 6351558574044977929 |        22 |       44 |     16 |     2 |       7 |            1 |             0 | False        |         120 | True           |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122866 |      34 |     88 |       44 |  6.35219e+18 | 6351558574044977929 |        23 |       45 |     16 |     2 |       7 |            1 |             0 | False        |           0 | True           |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
| 122949 |      20 |   1049 |       44 |  6.35219e+18 | 6351558574044977929 |        24 |       47 |     16 |     2 |       7 |            1 |             0 | False        |           0 | True           |                     1 |                          0 |                       0 |                         0 |                             0 |                        0 |                    0 |                        0 |                           0 |                         0 |                        0 |                         0 |                             0 |                      0 |                    0 |                    0 |                     0 |                      0 |                      0 |
<p><img src="https://plikimpi.krakow.pl//zalacznik/242464/4.jpg" alt="polish sign language"></p>
