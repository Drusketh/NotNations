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
```php
<?php

	$sql = "SELECT * FROM resources WHERE ID = ?;";
    $stmt = mysqli_stmt_init($ng);

    if (!mysqli_stmt_prepare($stmt, $sql)) {
        header("location: ../index.php?error=holyshitwtf");
        exit();
    }

    $uid = 1;

    mysqli_stmt_bind_param($stmt, "i", uid);
    mysqli_stmt_execute($stmt);

	$result = mysqli_stmt_get_result($stmt)
    $resultdata = mysqli_fetch_array($result, MYSQLI_ASSOC);

    echo json_encode ($resultdata);
    
    mysqli_stmt_close($stmt);
?>
```
Somehow transfer the data to Javascript arrays. 

```php
// include the php file that makes the requests to the db

<script>
	// Access the array elements
	var passedArray = <?php echo json_encode($resultdata); ?>;
	// Display the array elements
	for(var i = 0; i < passedArray.length; i++){
	    make the page look pretty and give me numbers
	}
</script>
```
Use JS and factory templates to fill out the page/widget with the factory objects

![[Pasted image 20221015235235.png]]