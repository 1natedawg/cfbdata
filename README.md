## CFB Power Rater

This is a little side experiment of mine to try and collect college football FBS statistics for analysis. My vision is for this is a multi-part process:

1) A mechanism to pull FBS statistical data into a database. Right now that's a Mongo database so we can esseentially keep everything as JSON.

2) A step to process data from the database and come up with a rating system, ultimately ending with each team having an average rating number.

3) In a given week, based on line data for upcoming games compared to the teams' rating averages. For example - a line has Team A -7.5 vs Team B, but our numbers show Team A's averages signifigantly lower than Team B, we highlight that matchup as a potential pick for Team B.


### A couple disclaimers:
- I'm no data analyst. The math and processing here is very fluid and will most likely change quite a bit along the way.
- I'm barely a developer. This is more an exercise in getting more comfortable with Python and data analysis than anything.


### How the processing works:
For each stat we include in the calculation:
    
    - Sort the list of teams based on that stat
    - The best team in that stat category gets n points, where n is the number of teams in the group.
    - The next best team in that category gets n-1 points, and so forth until the worst team gets 1 point.
    - If there's a configured multiplier for a stat, apply it to the team's point value. This allows us to adjust the weight a specific stat has on the overall calculation.
    - Add the final total to the team's total and to the total for ths bucket (offense/defense/etc)
    