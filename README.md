# mongoDB

1.Provide a query showing just the names (and nothing else) of the Italian restaurants.

    db.restaurants.find({cuisine: "Italian"}, {name: "1", _id: false})

2. Provide a query showing how many Bakeries have a name that start with M.

    db.restaurants.find({cuisine: "Bakery", name: /^M/}).length()

3. Provide a query showing the zip codes (and _id's) of all restaurants with the word "Ice" in their cuisine.

    db.restaurants.find({cuisine: /^Ice/}, {"address.zipcode": true})

4. Provide a query showing the street and street number of Chinese restaurants ordered by zip code.
    
    db.restaurants.find({cuisine: "Chinese"}, {"address.zipcode": 1, "address.building": true, "address.street": true}).sort({"address.zipcode": 1})

5. Show only the American restaurants in Manhattan.

    db.restaurants.find({cuisine: "American ", borough: "Manhattan"})

6. Provide a query showing the restaurants that have been graded exactly 4 times.
    
    db.restaurants.find({grades: {$size: 4}})

7. Provide a query showing only _id, name and 2 grades from each restaurant on Broadway.

    db.restaurants.find({"address.street": "Broadway"}, {name: "1", grades: {$slice: 2}})

8. Provide a query showing the 5 pizza restaurants in the Bronx with the highest score on an evaluation.

    db.restaurants.find({cuisine: "Pizza", borough: "Bronx"}).sort({"grades.score": -1}).limit(5)

9. Provide a query to find all of the restaurants in Brooklynn and list only the 21st-30th results when ordered alphabetically by name.

    db.restaurants.find({borough: "Brooklyn"}).sort({"name": 1}).skip(20).limit(10)

10. Provide a query that returns all pizza and Italian restaurants in reverse alphabetic order.

    db.restaurants.find({cuisine: "Italian", cuisine: "Pizza"}).sort({"name": -1})

