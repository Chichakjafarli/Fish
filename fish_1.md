You are assigned as a junior data analyst by the company in order to giveyour solutions to the problems described below. When trying to solve the
issues, read the problem statement and think carefully about what is being asked. Now, time to start!
1. Company has sold too many fish everyday. Each fish has a different weight. Company wants to know each species maximum and minimum of each fish.
```sql
create table fish(Species varchar(30),
				  Weight float,
				  Vertical_length float,
				  Diagonal_length float,
				  Cross_length float,
				  Height float,
				  Width float
);
select * from public.fish;
select max(weight) as max_weight,min(weight) as min_weight,species from public.fish group by species;
```

| max_weight | min_weight | species   |
|------------|------------|-----------|
| 1000       | 270        | Whitefish |
| 19.9       | 6.7        | Smelt     |
| 1000       | 242        | Bream     |
| 1650       | 200        | Pike      |
| 1100       | 5.9        | Perch     |
| 390        | 0          | Roach     |
| 300        | 55         | Parkki    |
2. The Company has many sold to much different fish and they want to see fish which height more than 15 and also width has to be more than 5.
```sql
select * from public.fish where height>15 and weight>5;
```
| species | weight | vertical_length | diagonal_length | cross_length | height  | width  |
|---------|--------|-----------------|-----------------|--------------|---------|--------|
| Bream   | 600    | 29.4            | 32              | 37.2         | 15.438  | 5.58   |
| Bream   | 610    | 30.9            | 33.5            | 38.6         | 15.633  | 5.1338 |
| Bream   | 575    | 31.3            | 34              | 39.5         | 15.1285 | 5.5695 |
| Bream   | 685    | 31.4            | 34              | 39.2         | 15.9936 | 5.3704 |
| Bream   | 620    | 31.5            | 34.5            | 39.7         | 15.5227 | 5.2801 |
| Bream   | 680    | 31.8            | 35              | 40.6         | 15.4686 | 6.1306 |
| Bream   | 700    | 31.9            | 35              | 40.5         | 16.2405 | 5.589  |
| Bream   | 725    | 31.8            | 35              | 40.9         | 16.36   | 6.0532 |
| Bream   | 720    | 32              | 35              | 40.6         | 16.3618 | 6.09   |
| Bream   | 714    | 32.7            | 36              | 41.5         | 16.517  | 5.8515 |
| Bream   | 850    | 32.8            | 36              | 41.6         | 16.8896 | 6.1984 |
| Bream   | 1000   | 33.5            | 37              | 42.6         | 18.957  | 6.603  |
| Bream   | 920    | 35              | 38.5            | 44.1         | 18.0369 | 6.3063 |
| Bream   | 955    | 35              | 38.5            | 44           | 18.084  | 6.292  |
| Bream   | 925    | 36.2            | 39.5            | 45.3         | 18.7542 | 6.7497 |
| Bream   | 975    | 37.4            | 41              | 45.9         | 18.6354 | 6.7473 |
| Bream   | 950    | 38              | 41              | 46.5         | 17.6235 | 6.3705 |

3. The company store has too many fish and each fish has its own 3 lengths. Company wants to see each species fish average lengths.
```sql
SELECT 
    ROUND(AVG(CAST(vertical_length AS NUMERIC)), 2) AS avg_vertical_length,
    ROUND(AVG(CAST(diagonal_length AS NUMERIC)), 2) AS avg_diagonal_length,
    ROUND(AVG(CAST(cross_length AS NUMERIC)), 2) AS avg_cross_length,
    species
FROM public.fish GROUP BY species;
```

| avg_vertical_length | avg_diagonal_length | avg_cross_length | species    |
|---------------------|---------------------|-------------------|-----------|
| 28.8                | 31.32               | 34.32             | Whitefish |
| 11.26               | 11.92               | 13.04             | Smelt     |
| 30.31               | 33.11               | 38.35             | Bream     |
| 42.48               | 45.48               | 48.72             | Pike      |
| 25.74               | 27.89               | 29.57             | Perch     |
| 20.65               | 22.28               | 24.97             | Roach     |
| 18.73               | 20.35               | 22.79             | Parkki    |

4. Company sees that some species sell too much. Company knows that species of fish start at “B” and height is more than 10 and smaller than 13.
 They want to all information about these fishes.
```sql
select * from public.fish where species like 'B%' and height between 10 and 13
```

| species | weight | vertical_length | diagonal_length | cross_length | height  | width   |
|---------|--------|-----------------|-----------------|--------------|---------|---------|
| Bream   | 242    | 23.2            | 25.4            | 30           | 11.52   | 4.02    |
| Bream   | 290    | 24              | 26.3            | 31.2         | 12.48   | 4.3056  |
| Bream   | 340    | 23.9            | 26.5            | 31.1         | 12.3778 | 4.6961  |
| Bream   | 363    | 26.3            | 29              | 33.5         | 12.73   | 4.4555  |
| Bream   | 430    | 26.5            | 29              | 34           | 12.444  | 5.134   |
| Bream   | 390    | 27.6            | 30              | 35           | 12.67   | 4.69    |


