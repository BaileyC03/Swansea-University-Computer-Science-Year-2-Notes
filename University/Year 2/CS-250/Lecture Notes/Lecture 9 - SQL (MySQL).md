#### MySQL and Set:
- MySQL doesnt have Minus (except in MariaDB) and Intersect
- This means we must write our queries in alternate ways

#### Union (MYSQL)
- Union removes duplicates
- Union all does not

#### Difference (MySQL)
- Use "Not in" or "Not exists" to replace the lack of a minus

#### Intersection (MySQL)
- Use "In" as there is no intersection

#### Natural Join (MySQL)
- Dont use natural join keywords >:(
- Consider inner join (google this)

#### Left Outer Join (MySQL)
- This is not an alternative to natural join as it includes all on the left and will put "null" for anything that doesnt exist on the other table
- This can be used in "minus" too as all that have "null" implies it is in one table not the other.

#### Cross Join:
Cartesian product

# LOOK UP DIVISION IN MYSQL THAT BITCH HARD
