Should be an administration page, different from a mod menu. This page should be for Developers only to add game elements in through forms.

### Factory Addition
* ##### Frontend
	* [x] Basic Functionality
	* [ ] Add a prompt before submitting the form
		* Make it show a preview of the factory made and allow the admin to make sure all looks good before adding it
* ##### Backend
	* [x] Needs to check if the name and at least one input and output are set
	* [x] Create a csv string for both costs and production of the factory. Iterate through the exploded $formdata array to find all occurrences of pcount and ccount, and then put them into their respective cost string.
	* [x] push to the factories table
		* Table should be formatted as such

| ID   | Name  | Cost | Produces | Maxlevel | Icon | 
| ---- | ----- | ---- | -------- | -------- | ---- |
| auto | 32str | text | text     | int      |      |
