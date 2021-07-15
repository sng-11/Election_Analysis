# Election Analysis

## Project Overview
The purpose of this analysis project is to use Python to write a script that can complete an election audit for a recent local congressional election. For the Colorado Board of Elections, the following needs to be extracted from the raw data: 

1. Total number of votes casted
2. List of candidates who received votes
3. Total number of votes for each candidate
4. Percentages of votes for each candidate
5. The winner by popular vote
6. Total number of votes for each county
7. County with the largest vote count 

In summary, this project uses a Python code to extract a Colorado election's results from a large amount of voting data. Information of candidates and counties are analyzed here.

## Resources
- Data Source: election_results.csv
- Software: Python 3.8.8, Visual Studio Code 1.57.1

## Election-Audit Results

### Summary Printout 
<img width="296" alt="Screen Shot 2021-07-15 at 1 22 48 AM" src="https://user-images.githubusercontent.com/84816495/125733305-ed59380c-59ca-4420-92da-6cec0634d202.png">

### Results based on Candidates

**Python Code Explanation:**
In order to determine the percentage of votes for each candidate, it is necessary to count the (a) total number of votes across all candidates, and (b) each candidate's vote count. Division of (b) over (a) will yield percentage. To count over every row in the data, it is necessary to use a for loop.

    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1
    
And to track each candidate, it is necessary to create an if statement within the for loop to only add a candidate's name to the list if it has not been previously added.

        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)
            
Finally, tracking a candidate's votes can be done by doing what was done above for total votes within the for loop:

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1

The analysis of the election shows that:
- There were 369,711 votes cast in this election.
- The candidates were:
    - Charles Casper Stockham
    - Diana DeGette
    - Raymon Anthony Doane
- The candidate results were:
    - Charles Casper Stockham received 23.0% of the vote and 85,213 number of votes.
    - Diana DeGette received 73.8% of the vote and 272,892 number of votes.
    - Raymon Anthony Doane received 3.1% of the vote and 11,606 number of votes.
- The winner of the election was:
    - ***Diana DeGette, who receieved 73.8% of the vote and 272,892 number of votes.***

### Results Based on Counties

**Python Code Explanation:**
In order to determine the vote count per county and which one had the highest vote count, a similar code as above was used. Within the same for loop, an if statement was used to add a county into list of participating counties if the name had not previously appeared before. This is done by:

        # 4a: Write an if statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in county_options:

            # 4b: Add the existing county to the list of counties.
            county_options.append(county_name)

And county votes were also calculated in a similar way, with:

    # 5: Add a vote to that county's vote count.
            county_votes[county_name] += 1

The winning county was determined by checking which county had the most votes compared to others. And an if statement was used to get the highest vote count among the county options:

    # 6f: Write an if statement to determine the winning county and get its vote count.
        if (county_votes[county_name] > county_voter_turnout):
            winning_county_count = county_votes[county_name]
            winning_county = county_name


## Election-Audit Summary

This Python script will be a useful template for the Colorado Board of Elections to have because it can be applied to other kinds of elections besides the state-wide congressional election. For example, this can be used on a federal level by substituting the counties for states. This script can also be used in an internal election within the Colorado Board, for example, instead of tracking counties voter counts, the board can track department voter counts to determine which department is most involved in the board's internal election.
