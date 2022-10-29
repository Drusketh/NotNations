
### Inputs
* Battle ID

### SQL Table
* Needs to include name of attackers and defenders, npc involvements having dedicated id.
* divison ids
* If unit data is saved, iterate through division data and get division relative unit id's, not absolute id's. This is to save precious data serverside
* Battle history like so: $avd-h,...$
	* attacker unit id = a
	* defender unit id = d
	* damage dealt = h
	* split on v - and ,
* Victor name

### Needs to return following information:
* Attacker and Defender Name
* Divisions involved
* Division data using json from [[getdivision.php]]
* Battle history string, interpret clientside with html or js