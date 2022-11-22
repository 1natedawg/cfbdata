## CFB Power Rater

taking some notes here, will clean up later


the idea is to have a final dataframe with the best values on top, worst on bottom
points start at len(# of FBS teams)
for each stat:
    sort all teams by that stat (asc/desc in config determines sort)
    first team gets len(# of FBS teams) points, second team gest n-1, so on until the worst team gets 1 pt
    apply multiplier in config.json to determine statistical weight
    add final value to bucket total and overall total

