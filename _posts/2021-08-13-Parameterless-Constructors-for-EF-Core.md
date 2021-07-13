> All Entities linked to EntityFramework must have a Default Constructor.

I added Unit Testing to my A2 project Asset Manager's domain models the other day. Because I didn't want to leave all the models' parameterless constructors uncovered, I removed all the empty parameterless constructors and only tested the parameterized ones.

The Debug session then threw some *property binding* error when I tried to `GET` some entity using **SWAGGER**. This was fixed by adding back all the removed parameterless constructors. And I understood now [why](https://stackoverflow.com/a/30874201) they are necessary even though they would do nothing (because they are parameterless and empty) as I thought.

> When Entity Framework maps from a database query to your Entities it uses the default constructor to instantiate a new instance of your Entity to fill it with the data retrieved from the database.
>
>If you don't have a default constructor Entity Framework doesn't know how to create an instance of it and throws the exception

