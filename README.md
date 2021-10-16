# Overview of Election Audit using Python
The purpose of this audit is to automate the analysis of a US congressional election in Colorado. I’ve been tasked with reporting the vote count of the election results. The election audit includes total votes, total number of votes for each candidate, the percentage of votes per candidate, the total number of votes per county, the percentage of votes per county, and the winner of the election based on the popular vote.

## Election Audit Results
A total of 369,711 votes were casted resulting in Diana DeGette as the winning candidate, and Denver county the couty with the largest voter turnout.
### Election Audit image
<img width="188" alt="election_audit_results" src="https://user-images.githubusercontent.com/87162266/133898646-de0d7911-b1bc-45eb-9a8e-84a2ffae9d1a.PNG">

### Election Audit Code

I refracted this [code](https://github.com/DWashington3/Election_Analysis/blob/0e69df151c9b605937a95ce50e95b402bd464828/PyPoll_Challenge.py) by creating an if statement that tracked each unique county's name and vote count. After, the text file is now opened to print the total number of votes from the election. Within that ", with" statement I created another for loop that calculates the percentage of votes in each county. In the for loop, I created two if statements that defined the county with the winning percentage, and the county with the greatest number of votes.




    for county in county_votes:
        # 6b: Retrieve the county vote count.
        c_votes= float(county_votes[county])
        # 6c: Calculate the percentage of votes for the county.
        county_percentage= (c_votes)/(total_votes)*100

         # 6d: Print the county results to the terminal.
        county_results= (f"{county}:{county_percentage:.1f}%({c_votes:,})\n")

        print(county_results)
         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
        
         # 6f: Write an if statement to determine the winning county and get its vote count.
        if county_percentage> county_winning_percentage:
            county_winning_percentage=county_percentage
            winning_county=county

        
        if c_votes > county_winning_count:
           county_winning_count= c_votes
         

    # 7: Print the county with the largest turnout to the terminal.
    print(
            f"-------------------------\n"
            f"Largest county turnout: {winning_county}\n"
            f"-------------------------\n")
        

    # 8: Save the county with the largest turnout to a text file.
    txt_file.write(f"-------------------------\n"
            f"Largest county turnout: {winning_county}\n"
            f"-------------------------\n")






## Election Audit Summary
### Application 1
Utilizing Python to automate the election audit saves time and money. The script used for the US congressional election in Colorado can be applied to other elections. This is possible by modifying the code. If another state had a US congressional election we could simply modify the data being pulled and run everything as the same. So instead of “election_results” which is solely applicable to the Colorado data. For a Florida US congressional audit, the file_to_load code would pull Florida’s information which may be saved as “florida_election_results

<img width="251" alt="code_mod" src="https://user-images.githubusercontent.com/87162266/133905489-16fb4955-38c9-4767-9809-c365ec8fea35.PNG">

### Application 2
To apply the same automation on a larger scale, determining the popular voting party per state.  To do so with this code, the county variables would be defined in terms of states. We’d add and initialize new variables republican_votes=0 and democratic_votes =0. Next, we can create a loop to iterate in our dictionary of state votes. In that loop create an elif statement that could count “Democratic candidate 1” and “ Democratic candidate 2” name as a count in the democratic_vote variable. But if not one of these candidates’ names it will count toward the republican_votes variable. Assuming the two largest voting parties are the democratic and republican party.
