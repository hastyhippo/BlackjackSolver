# BlackjackSolver

This is a solver using MonteCarlo methods intended to find the EV of blackjack and to find the optimal strategy at each node of the game tree in standard Casino Blackjack.

It accomplishes this by simulating the game, calculating the ev of each action as if each card was equally likely to come out by running the game many many times from each position to estimates its ev. It dynamically stores the EV of each position in a hashmap, as each position can be hashed by its: Count, Whether an Ace is present, if the player has doubled down, etc. It then goes through every action and every possibility of the game tree to find the optimal strategy at each node and then prints it out at the end.

EV of each position.

WITHOUT ACE: 

```
  P\D       2       3       4       5       6       7       8       9      10      11
----------------------------------------------------------------------------------------
    6 | -0.1415 -0.1091 -0.0679 -0.0359  0.0018 -0.1539 -0.2169 -0.2891 -0.3341 -0.3386
    7 | -0.1093 -0.0777 -0.0460 -0.0112  0.0294 -0.0720 -0.2094 -0.2792 -0.3193 -0.3475
    8 | -0.0274  0.0094  0.0349  0.0711  0.1039  0.0785 -0.0609 -0.2051 -0.2438 -0.2582
    9 |  0.0724  0.0972  0.1236  0.1546  0.1876  0.1705  0.0985 -0.0469 -0.1521 -0.1202
   10 |  0.1777  0.2060  0.2269  0.2548  0.2812  0.2550  0.2004  0.1204  0.0292  0.0334
   11 |  0.2354  0.2580  0.2790  0.3062  0.3300  0.2898  0.2292  0.1614  0.1227  0.1045
   12 | -0.2552 -0.2339 -0.2142 -0.1642 -0.1194 -0.2155 -0.2709 -0.3361 -0.3797 -0.3826
   13 | -0.2886 -0.2552 -0.2058 -0.1786 -0.1164 -0.2706 -0.3234 -0.3844 -0.4233 -0.4264
   14 | -0.2936 -0.2390 -0.2016 -0.1712 -0.1208 -0.3222 -0.3717 -0.4290 -0.4646 -0.4683
   15 | -0.2932 -0.2508 -0.2110 -0.1662 -0.1328 -0.3707 -0.4166 -0.4694 -0.5033 -0.5054
   16 | -0.2910 -0.2596 -0.1930 -0.1652 -0.1284 -0.4159 -0.4585 -0.5065 -0.5334 -0.5405
   17 | -0.1472 -0.1175 -0.0956 -0.0498 -0.0097 -0.1119 -0.3768 -0.4107 -0.4267 -0.5140
   18 |  0.1052  0.1529  0.1624  0.2041  0.2304  0.3943  0.1023 -0.1758 -0.1633 -0.2123
   19 |  0.3827  0.3892  0.4089  0.4303  0.4583  0.6138  0.5949  0.2944  0.0598  0.1922
   20 |  0.6276  0.6523  0.6534  0.6704  0.6758  0.7700  0.7976  0.7608  0.5609  0.5964
```
WITH ACE:
```
  P\D       2       3       4       5       6       7       8       9      10      11
----------------------------------------------------------------------------------------
   13 |  0.0456  0.0720  0.1032  0.1284  0.1662  0.1207  0.0527 -0.0352 -0.1027 -0.0956
   14 |  0.0202  0.0527  0.0822  0.1086  0.1448  0.0775  0.0119 -0.0726 -0.1376 -0.1310
   15 | -0.0021  0.0288  0.0593  0.0900  0.1226  0.0352 -0.0283 -0.1096 -0.1722 -0.1658
   16 | -0.0223  0.0067  0.0451  0.0721  0.1055 -0.0069 -0.0680 -0.1459 -0.2046 -0.2004
   17 | -0.0005  0.0286  0.0559  0.0876  0.1228  0.0511 -0.0728 -0.1441 -0.1974 -0.2171
   18 |  0.1049  0.1368  0.1817  0.1837  0.2399  0.3901  0.0989 -0.0961 -0.1385 -0.1520
   19 |  0.3806  0.4025  0.4199  0.4400  0.4442  0.6082  0.5840  0.2909  0.0661  0.1888
   20 |  0.6385  0.6509  0.6476  0.6724  0.6769  0.7799  0.7930  0.7600  0.5536  0.6138
   21 |  0.8802  0.8837  0.8855  0.8921  0.8902  0.9275  0.9294  0.9390  0.9642  0.9083
```
For an average EV of -0.0137

The following are heatmaps generated in MATLAB which visualise the EV of different spots:
![image](https://github.com/user-attachments/assets/46cf96bc-83bf-4a24-bcb4-d500ef542e32)

![image](https://github.com/user-attachments/assets/1200bff2-0eba-404b-ad86-88c15b08705a)

These results align with common blackjack strategy.

And the appropriate action to take to maximise the EV.
```
  P\D       2       3       4       5       6       7       8       9      10      11
----------------------------------------------------------------------------------------
    4 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
    5 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
    6 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
    7 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
    8 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
    9 |     HIT  DOUBLE  DOUBLE  DOUBLE  DOUBLE     HIT     HIT     HIT     HIT     HIT
   10 |  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE     HIT     HIT     HIT
   11 |  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE  DOUBLE
   12 |     HIT     HIT   STAND   STAND   STAND     HIT     HIT     HIT     HIT     HIT
   13 |   STAND   STAND   STAND   STAND   STAND     HIT     HIT     HIT     HIT     HIT
   14 |   STAND   STAND   STAND   STAND   STAND     HIT     HIT     HIT     HIT     HIT
   15 |   STAND   STAND   STAND   STAND   STAND     HIT     HIT     HIT     HIT     HIT
   16 |   STAND   STAND   STAND   STAND   STAND     HIT     HIT     HIT     HIT     HIT
   17 |   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND
   18 |   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND
   19 |   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND
   20 |   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND
```
WITH AN ACE:
```
  P\D       2       3       4       5       6       7       8       9      10      11
----------------------------------------------------------------------------------------
   13 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
   14 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
   15 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
   16 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
   17 |     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT     HIT
   18 |   STAND   STAND   STAND   STAND   STAND   STAND   STAND     HIT     HIT     HIT
   19 |   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND
   20 |   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND
   21 |   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND   STAND
```

