# BigData-IPL-Simulation

## Introduction

The Indian Premier League (IPL) is a Twenty-20 cricket tournament league established with the objective of promoting cricket in India and thereby nurturing young and talented players. The league is an annual event where teams representing different Indian cities compete against each other. Every year it brings happiness, joy, excitement and uncertainty among the cricket fans. What would it be like to predict which team is going to have the upper hand in the match well before the match? It would be exciting to use mathematics, statistics and computer science techniques to come up with a system which can give a ball-by-ball prediction of a match given any 2 random teams.

## Problem Statement
IPL match analysis using the data from all the IPL matches from the beginning till date. Our main motive is to predict the score and the match outcome. Here we use a clustering method choosing a random probability to simulate the ball-by-ball match outcomes given a random set of two teams.

## Design of Solution
**Step 1:**

Step 1 of this project involves basically two tasks- data collection and clustering of players.
The main ipl.csv file was directly available on the website so we simply downloaded it. The batting.csv and the bowling.csv files were to be made using BeautifulSoup for data extraction about which we have already explained in the subtopic - Challenges.

The second task in step 1 was the clustering of players according to their performance in batting and bowling. We have used K-means clustering for clustering batsmen and bowlers into clusters. We have divided batsmen and bowlers into 10 clusters each. After the clustering process we are creating two new CSV files- bat_clusters.csv and bowl_clusters.csv which contain names of players and their predicted cluster numbers. 

**Step 2:**

Once the Batting and Bowling clusters were obtained,  cluster vs cluster statistics  was calculated using the main dataset which had a ball by ball outcome of all matches from 2008-2021. 
This was done by maintaining a dictionary of batsmen cluster vs bowler cluster parameter totals(0s,1s,2s,3s,4s,6s,wickets). Every time a new combination was encountered, we found the batsman cluster number and the bowler cluster number and added the parameters to the corresponding cluster combination. Finally probabilities of scoring 0s,1s,2s,3s,4s,6s,wickets were obtained for every cluster combination by dividing by the total number of balls.

A summary statistics file is also generated for every batsman-bowler combination encountered in the main dataset, which contains the probabilities of scoring 0s,1s,2s,3s,4s,6s and wickets, when that particular combination faces each other. 

We wrote a python code to simulate an entire IPL match using ball by ball prediction. To predict the outcome of a ball, we searched for the batsman-bowler combination in the summary statistics file. 
A list of cumulative probabilities is constructed from the probabilities obtained. A random is generated and the outcome is decided based on the range of cumulative probabilities in which it falls. The outcome could be 0,1,2,3,4,6 or a wicket. This is repeated for all balls until 20 overs are up or there are no wickets left. An additional way of a wicket falling is also added. We write the outcome of every ball into a CSV file. 
