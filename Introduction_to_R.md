# Introduction to R

# Basics

## Calculs :
- comments : #
- puissance : 3^2
- modulo : 3%%9
- decimals : 4.5

## Variables : 
-  `my_apples <- 5 `
-  `my_oranges <- "six" `
- ` my_fruit <- my_apples + my_oranges `

## Class
-  `class(my_oranges)` renvoie text

# Vectors
-  `numeric_vector <- c(1, 2, 3)`
-  `character_vector <- c("a", "b", "c")`
## noms 
-  `some_vector <- c("John Doe", "poker player")`
-  `names(some_vector) <- c("Name", "Profession")`
## assigner variable à un vecteur 
```
// The variable days_vector

days_vector <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
Assign the names of the day to roulette_vector and poker_vector
names(poker_vector) <-   days_vector
names(roulette_vector) <- days_vector
```
## additionner vecteurs
```
> A_vector <- c(1, 2, 3)
> B_vector <- c(4, 5, 6)
> # Take the sum of A_vector and B_vector
> total_vector <- A_vector + B_vector
> # Print out total_vector
> total_vector
```
## somme des éléments d’un vecteur
`> total_poker <- sum(poker_vector)`
## comparaison (renvoie TRUE ou FALSE)
```
> # Check if you realized higher total gains in poker than in roulette 
> total_poker>total_roulette
```
## sélection d’éléments d’un vecteur
```
> # Define a new variable based on a selection
> poker_wednesday <- poker_vector[3]
> # Define a new variable based on a selection of items 2,3,4
> poker_midweek <- poker_vector[c(2,3,4)]
> # Define a new variable based on a selection of items 2 to 5
> roulette_selection_vector <- roulette_vector[c(2:5)]
> # Select poker results for Monday, Tuesday and Wednesday
> poker_start <- poker_vector[c("Monday","Tuesday","Wednesday")]
```
## Moyenne des éléments d’un vecteur
```
> # Calculate the average of the elements in poker_start
> mean(poker_start)
```
## Test sur éléments d’un vecteur
```
> # Which days did you make money on poker?
> selection_vector <- poker_vector > 0
> # Print out selection_vector
> selection_vector
   Monday   Tuesday Wednesday  Thursday    Friday 
     TRUE     FALSE      TRUE     FALSE      TRUE
``` 
## Ne garder que les éléments satisfaisant le test :
```
> # Select from poker_vector these days
> poker_winning_days <- poker_vector[selection_vector]
```
# Matrices
## Constructions d’une matrice :
```
> # Construct a matrix with 3 rows that contain the numbers 1 up to 9
> matrix(1:9,byrow=TRUE,nrow=3)
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]    4    5    6
[3,]    7    8    9
```

## Analyse de matrices
```
> # Box office Star Wars (in millions!)
> new_hope <- c(460.998, 314.4)
> empire_strikes <- c(290.475, 247.900)
> return_jedi <- c(309.306, 165.8)
> # Create box_office
> box_office <- c(new_hope,empire_strikes,return_jedi)
> # Construct star_wars_matrix
> star_wars_matrix <- matrix(box_office,byrow=TRUE,nrow=3)
```

## Nommage des lignes et colonnes d’une matrice
```
rownames(my_matrix) <- row_names_vector
colnames(my_matrix) <- col_names_vector
```

## Somme des lignes d’une matrice :
`rowSums(my_matrix)`

## ajout d’une colonne contenant un vecteur à une matrice 
```
You can add a column or multiple columns to a matrix with the cbind() function, which merges matrices and/or vectors together by column. For example: 
big_matrix <- cbind(matrix1, matrix2, vector1 ...)
```

## même chose avec les lignes
`rbind(matrice1,matrice2,…)`

##  sélection d’éléments d’une matrice
```
> my_matrix[1,2] selects the element at the first row and second column.
> my_matrix[1:3,2:4] results in a matrix with the data on the rows 1, 2, 3 and columns 2, 3, 4.
> my_matrix[,1] selects all elements of the first column.
> my_matrix[1,] selects all elements of the first row.
```

## travaux sur les matrices
```
> all_wars_matrix
                           US non-US
A New Hope              461.0  314.4
The Empire Strikes Back 290.5  247.9
Return of the Jedi      309.3  165.8
The Phantom Menace      474.5  552.5
Attack of the Clones    310.7  338.7
Revenge of the Sith     380.3  468.5
> 
> # Select the non-US revenue for all movies
> non_us_all <- all_wars_matrix[,2]
>   
> # Average non-US revenue
> mean(non_us_all)
[1] 347.9667
>   
> # Select the non-US revenue for first two movies
> non_us_some <- all_wars_matrix[1:2,2]
>   
> # Average non-US revenue for first two movies
> mean(non_us_some)
[1] 281.15
```

## Opérations sur les matrices
```
For example, 2 * my_matrix multiplies each element of my_matrix by two.
```

## Opération entre matrices
```
> # Estimated number of visitors
> visitors <- all_wars_matrix / ticket_prices_matrix
> 
> # US visitors
> us_visitors <- visitors[,1]
> 
> # Average number of US visitors
> mean(us_visitors)
[1] 75.01401
```

# Facteurs

```
The term factor refers to a statistical data type used to store categorical variables. The difference between a categorical variable and a continuous variable is that a categorical variable can belong to a limited number of categories. A continuous variable, on the other hand, can correspond to an infinite number of values.
A good example of a categorical variable is the variable 'Gender'. A human individual can either be "Male" or "Female", making abstraction of inter-sexes. So here "Male" and "Female" are, in a simplified sense, the two values of the categorical variable "Gender", and every observation can be assigned to either the value "Male" of "Female".
```

## Nominal categorical variable
```
> # Animals
> animals_vector <- c("Elephant", "Giraffe", "Donkey", "Horse")
> factor_animals_vector <- factor(animals_vector)
> factor_animals_vector
[1] Elephant Giraffe  Donkey   Horse   
Levels: Donkey Elephant Giraffe Horse
```

## Ordinal categorical variable
```
> # Temperature
> temperature_vector <- c("High", "Low", "High","Low", "Medium")
> factor_temperature_vector <- factor(temperature_vector, order = TRUE, levels = c("Low", "Medium", "High"))
> factor_temperature_vector
[1] High   Low    High   Low    Medium
Levels: Low < Medium < High
```

## Level’s names
`levels(factor_vector) <- c("name1", "name2",...)`

## quick overview of the contents of a variable:
`summary(my_var)`
## comptabilisation des occurrences d’un vecteur par levels :
```
> # Build factor_survey_vector with clean levels
> survey_vector <- c("M", "F", "F", "M", "M")
> factor_survey_vector <- factor(survey_vector)
> levels(factor_survey_vector) <- c("Female", "Male")
> factor_survey_vector
[1] Male   Female Female Male   Male  
Levels: Female Male
```

## ordonner des facteurs
```
> # Create speed_vector
> speed_vector <- c("fast", "slow", "slow", "fast", "insane")
> 
> # Convert speed_vector to ordered factor vector
> factor_speed_vector <- factor (speed_vector,ordered=TRUE,levels=c("slow","fast","insane"))
> 
> # Print factor_speed_vector
> factor_speed_vector
[1] fast   slow   slow   fast   insane
Levels: slow < fast < insane
> summary(factor_speed_vector)
  slow   fast insane 
     2      2      1 
```

# Data frames
```
A data frame has the variables of a data set as columns and the observations as rows. This will be a familiar concept for those coming from different statistical software packages such as SAS or SPSS.
```

## head(mydataset) : premières lignes du data set

## tail (mydataset) : dernières lignes du data set

## str (mydataset) : structure du data set

## construction d’un data frame :
```
> # Definition of vectors
> name <- c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune")
> type <- c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
            "Terrestrial planet", "Gas giant", "Gas giant", "Gas giant", "Gas giant")
> diameter <- c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
> rotation <- c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
> rings <- c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)
> 
> # Create a data frame from the vectors
> planets_df <- data.frame(name,type,diameter,rotation,rings)
```

## sélection dans un data frame :
- avec num ligne / colonne
```
> Print out diameter of Mercury (row 1, column 3)
> planets_df[1,3]
```

- toute une ligne / toute une colonne
`> Print out data for Mars (entire fourth row)
planets_df[4,]`
- toute la colonne "diameter"
```
> # Select first 5 values of diameter column by naming it
> planets_df[1:5,"diameter"]
[1]  0.382  0.949  1.000  0.532 11.209
```

- raccourcis pour sélectionner toute une colonne : planets_df$diameter
```
> # Select the rings variable from planets_df
rings_vector <- planets_df$rings
>   * ne garder que les planets dont le rings est TRUE :
> planets_df[rings_vector, ]
```

- subset de data frame : subset(my_df, subset = some_condition)
```
> # Select the planets with rings
> subset(planets_df, subset = rings)
```
ou
```
> # Select planets with diameter < 1
> subset(planets_df,diameter<1)
```

we can use the output of order(a) to reshuffle a:
`> a[order(a)]`

##  trier un data frame par colonne
```
># Use order() to create positions
> positions <-  order(planets_df$diameter)

># Use positions to sort planets_df
> planets_df[positions,]
```

# EN BREF
- Vectors (one dimensional array): can hold numeric, character or logical values. The elements in a vector all have the same data type.
    `> my_vector <- c(value1,value2,value3,…)`
- Matrices (two dimensional array): can hold numeric, character or logical values. The elements in a matrix all have the same data type.
   ` > matrix(1:9,byrow=TRUE,nrow=3)`
- Data frames (two-dimensional objects): can hold numeric, character or logical values. Within a column all elements have the same data type, but different columns can be of different data type.
    `> my_data_frame <- data.frame(vector1,vector2,vector3,…)`

# LISTS
`my_list <- list(comp1, comp2 ...)`

##  nommage des éléments d’une liste : 
```
> my_list <- list(your_comp1, your_comp2)
> names(my_list) <- c("name1", "name2")
```

ou plus directement : `shining_list <- list(moviename = mov,actors=act,reviews=rev)`

## sélection des éléments d’une liste
```
> # Print out the vector representing the actors
> shining_list$actors

> # Print the second element of the vector representing the actors
> shining_list$actors[2]
```

##  ajout d’une colonne year à notre liste avec la valeur 1980
```
> # We forgot something; add the year to shining_list
> shining_list_full <- c(shining_list,year=1980)
```
