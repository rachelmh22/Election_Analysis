# Election Audit Analysis


## Overview of Election Audit

### Purpose

The purpose of this project is to audit the election results for US congressional precinct in Colaroda. The initial analysis required us to report on the total votes, and the number and percentage of votes to each candidate, as well as the winning candidate and their results. After this information was analyzed and reported, the election commission has asked for additional data. This data includes the voter turnout for each county, the percentage of votes from each county, and the county with the highest turnout. Therefore, the purpose of this project is to add this additional data and complete the analysis of the election results. 


## Election-Audit Results 

- There was a total of 369,711 votes cast in this congressional election. The following code allowed us to get the total votes by initializing the total vote count to 0 then using a for loop to go through the election data and add a vote to the total count for each vote in the data.
```
total_votes = 0
…
for row in reader: 
	total_votes = total_votes + 1
```

- The following is a breakdown of the number of votes and the percentage of votes for each county, as well as the code used to get these results:
   - Jefferson county received 38,855 votes, which is 10.5% of the total votes
   - Denver county received 306,055 votes, which is 82.8% of the total votes
   - Arapahoe county received 24,801 votes, which is 6.7% of the total votes
```
county_options = []
county_votes = {}
…
winning_county = ""
winning_county_count = 0
winning_county_percentage = 0
…
for row in reader:
	county_name = row[1]
	if county_name not in county_options:
		county_options.append(county_name)
		county_votes[county_name] = 0
	county_votes[county_name] += 1
…
for county_name in county_votes:
	votes = county_votes[county_name]
	vote_percentage = float(votes) / float(total_votes) * 100
…
	if (votes > winning_county_count) and (vote_percentage > winning_county_percentage):
		winning_county_count = votes
		winning_county_percentage = vote_percentage
		winning_county = county_name
```

- Denver county had the largest number of votes

- The following is a breakdown of the number and percentage of votes that each candidate received, as well as the code used to get these results:
   - Charles Casper Stockham received 85,213 votes, which is 23.0% of the total votes
   - Diana DeGette received 272,892 votes, which is 73.8% of the total votes
   - Raymon Anthony Doane received 11,606 votes, which is 3.1% of the total votes
```
candidate_options = []
candidate_votes = {}
…
winning_candidate = ""
winning_count = 0
winning_percentage = 0
…
for row in reader:
	candidate_name = row[2]
	if candidate_name not in candidate_options:
		candidate_options.append(candidate_name)
		candidate_votes[candidate_name] = 0
	candidate_votes[candidate_name] += 1
…
for candidate_name in candidate_votes:
	votes = candidate_votes.get(candidate_name)
	vote_percentage = float(votes) / float(total_votes) * 100
…       
	if (votes > winning_count) and (vote_percentage > winning_percentage):
		winning_count = votes
		winning_candidate = candidate_name
		winning_percentage = vote_percentage
```

- Diana DeGette won the election with a vote count of 272,892, which is 73.8% of the total votes


## Election-Audit Summary
