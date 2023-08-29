# Data_Analyst_Portfolio_5
A look into some data analytics of a comparative kind using Pokemon stats. For people who don't know much about Pokemon stats this will serve as an easy to digest representation of the different types' standing
compared to one another.

By now I am getting more comfortable with the processes involved and so began by posing questions before I start to do anything with the data.
This will be based on presentation skills where an interactive page is created which looks at each type (by clicking on it) and shows comparisons to other types and the overall average.

==================================================================================

The first step was to create a treemap which was the best visual way to click on each type and see the rest of the page change. However, the data has two columns so I needed a way to create a treemap from the cumulative column values. 
I can't create a single column and adding type 2 to the type values in the treemap makes it unreadable. Instead I need to count the distinct values and put them in a new table done via:
DistinctValues = UNION(SELECTCOLUMNS('PokemonStats', "Type", 'PokemonStats'[Type1]), SELECTCOLUMNS('PokemonStats', "Type", 'PokemonStats'[Type2]))

This table is a single column of all the types, so not usable yet. Creating a new table:
CountTable = SUMMARIZE(DistinctValues, [Type], "Count", COUNTROWS('DistinctValues')) allows me to creat a treemap of the data combined.

In the Model View I then do two "Many to One" relatsionships and now clicking on the type in the tree map changes the rest of the data on the page.





