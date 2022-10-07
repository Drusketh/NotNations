# Resource Buildings/Factories

### Storing user data
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
	* This could be more space efficient than the previous methods if and only if I used some form of comma separated string that could later be exploded into the constituent factories, but probably not the smartest idea since it's probably easier to mess up than the above methods

			Think "farm,12,4,|,stonecutter,0,1,|,supergrass-producer,2560,5". Explode on | to obtain the values for each factory type, explode on commas and save to arrays/variables
	
### Data display

Retrieve the entire row of the table containg factory data. [like this](https://www.php.net/manual/en/mysqli-result.fetch-array.php)
Somehow transfer the data to Javascript arrays. [like this](https://www.geeksforgeeks.org/how-to-pass-a-php-array-to-a-javascript-function/)

```php
<?php
	// Create an array
	$sampleArray = array(
	    0 => "Geeks", 
	    1 => "for", 
	    2 => "Geeks", 
	)
?>
<script>
	// Access the array elements
	var passedArray = <?php echo json_encode($sampleArray); ?>;
	// Display the array elements
	for(var i = 0; i < passedArray.length; i++){
	    document.write(passedArray[i]);
	}
</script>
```
Use JS and factory templates to fill out the page/widget with the factory objects