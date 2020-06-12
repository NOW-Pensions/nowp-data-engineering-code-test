# NOW: Pensions Data Engineering Code Test

### Instructions
For questions 1-2 you are free to choose Python 3.x or Java 11.

* Do not use any third party dependencies except PyTest for Python, and JUnit/Hamcrest for Java.
* If using Java, please use Java 11 and the included build.gradle
* Code should be covered with adequate tests
* Code should be readable and clean
* For question 3, you can provide a (clear) photo/scan of your diagram, or use https://dbdiagram.io/ and share your diagram.
* For question 4 please provide a .sql file with your queries inside. Please state which SQL dialect you used.
* For question 5 please include a text file containing your answer.

### Question 1: 
Implement a function that takes three lists of strings as parameters. The first argument is a list of words that can be used as a subject in a sentence, the second – as a predicate, and the third – as an object. The function must return a string that contains all the sentences in the alphabetical order that can be constructed using the provided subjects, predicates and objects. (Note that the words in the list of subjects are not necessarily in the alphabetical order, and the same applies to the lists of predicates and objects.) Each sentence must be ended by ”.” and the sentences must be separated by ” ”. (Alphabetical order has usual and common meaning, but if you have doubts about it, see test cases below for examples.)

#### Indicative test cases (Python):

``` python 
assert generate_sentences(["Mark", "Mary"], ["hates", "loves"], ["apples", "bananas"])) == "Mark hates apples. Mark hates bananas. Mark loves apples. Mark loves bananas. Mary hates apples. Mary hates bananas. Mary loves apples. Mary loves bananas."
```

``` python
assert generate_sentences(["Vlad", "John"], ["drives"], ["car", "motorcycle", "bus"])) == "John drives bus. John drives car. John drives motorcycle. Vlad drives bus. Vlad drives car. Vlad drives motorcycle."
```

#### Indicative test cases (Java 11):

``` java
assertThat(generateSentences(List.of("Mark", "Mary"), List.of("hates", "loves"), List.of("apples", "bananas")), is("Mark loves apples. Mark loves bananas. Mary hates apples. Mary hates bananas. Mary loves apples. Mary loves bananas."));
```

``` java
assertThat(generateSentences(List.of("Vlad", "John"), List.of("drives"), List.of("car", "motorcycle", "bus")), is( "John drives bus. John drives car. John drives motorcycle. Vlad drives bus. Vlad drives car. Vlad drives motorcycle."));
```

### Question 2: 
Implement a class Airplane that keeps track of the following features of an airplane:

* consumption: an integer representing number of litres consumed per km of distance
* position (x, y): a pair of integers representing a position of the plane on a map. Can be a tuple if chosen language supports tuples (assume that the airplane can only be in one of the positions of the 1 km x 1 km grid)
* fuel level: a floating point number representing the current fuel level in litres

##### Implement the following methods:

* `constructor`: takes four integer parameters (in the specified sequence) `initX, initY, consuption and initial fuel level` where initX/initY represents initial location of the plane, cons represents the consumption (litre/km) and initial fuel level represents the initial fuel level.

* `goto`: takes two integer parameters X and Y representing the location where the plane needs to go to. If the airplane has enough fuel to travel there from its current location, the method moves it there, updates remaining fuel level, and returns True. Otherwise, the plain does not move and False is returned.

* `refuel`: takes one integer parameter indicating how many litres of fuel are added. No value returned.

Assume that the airplane travels in a direct line between two positions (X1, Y1) and
(X2, Y2). The distance between two locations is computed as the square root of ((X2 − X1)^2 + (Y 2 − Y 1)^2)

### Question 3:
Design an Entity-Relationship diagram for the specification below & briefly explain your choices.

`
We want a database for a university department. The database should record details of students, their enrolment in academic programmes (e. g., MSc Data Science) and details about the academic programmes, in particular, which modules are offered in each academic year. Students will be able to enroll in in more than one progamme, but not in the same year. Each module is taught by an instructor within an academic year, within a programme. For each module it should be possible to retrieve the name of the instructor and the number of credits associated with it. Finally, it should be possible to query the database to find out which students have ever taken a module with a given instructor.
`

### Question 4: 
Consider the following relational database tables to store information about athletes and their birthplaces.

#### City

|city_id|city_name|city_country|city_population|city_hemisphere|
|:-----:|:-------:|:----------:|:-------------:|:-------------:|
|1      |Sao Paulo| Brazil| 12110000| S|
|2      |Toronto |Canada |2732000| N|

#### Athletes

|athlete_id|athlete_first_name|athlete_last_name|athlete_birthplace|athlete_sex|
|:--------:|:----------------:|:---------------:|:----------------:|:---------:|
|1 |Neymar |Silva| 1| M|
|2 |Natalie |Spooner |2| F|

##### Table “City” description: 
“city_id” is primary key and numeric,
“city_population” is numeric, while “city_name”, “city_country” and
“city_hemisphere” are text fields.

##### Table “Athletes” description: 
“athlete_id” is primary key and numeric,
“athlete_birthplace” is numeric, while “athletes_first_name”,
“athletes_last_name”, “athletes_sex” are text fields. The
“athlete_birthplace” is a foreign key and references the “city_id” field
of the “City” table.

#### Give SQL statements for the following:
a. Insert a new city to include, id: 3, name: Tokyo, Country: Japan, Population: 9,2 million, Hemisphere: North.

b. Update Tokyo population to 9,73 million.

c. Query the city table for the cities in the northern hemispher and with population greater than 10 million.

d. Query the city table for the sum of the populations of cities in the northern hemisphere.

e. Query for athletes first name, last name and birth place.

f. Query for all athletes who were born in the southern hemisphere. 

g. Query for female athletes born in a city with population over 5 million.

h. Query for the athlete born in a city that has the highestpopulation.

### Question 5:
Breifley explain (one paragraph) the CAP theorem (Brewer, 2000), and give a example where A is sacrificed, and an example where C is sacrificed.

