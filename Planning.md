# Planning

### Resource Buildings/Factories
	There are several options for making these in the backend
	
1. Dedicated Factory Table, similar to resource table
	* In this dedicated table, there can be a uid entry and 3 columns for every factory in the game. These 3 columns for N factories would be formatted as

		| uid | fac1name      | fac1count | fac1level | ... | facNname | facNcount | facNlevel |
		| --- | ------------- | --------- | --------- | --- | -------- | --------- | --------- |
		| 1   | cowmilker3000 | 265       | 4         | ... | farm     | 2560      | 5         |
	* The slightly more efficient way would be a table with all factories in the game, and only 2 columns per factory. This would be written like:

		| uid | fac1count      | fac1level | fac2count | fac2level | ... | facNcount | facNlevel |
		| --- | ------------- | --------- | --------- | --- | -------- | --------- | --------- |
		| 1   | 12 | 4       | 0         | 1 | ...     | 2560      | 5         |
2. Include them in the user table or nation table. 
	* This could be more space efficient than the previous methods if and oly if I used some form of comma separated string that could later be exploded into the constituent factories, but probably not the smartest idea since it's probably easier to mess up than the above methods

			Think "farm,12,4,|,stonecutter,0,1,|,supergrass-producer,2560,5". Explode on | to obtain the values for each factory type, explode on commas and save to arrays/variables
	
3. 