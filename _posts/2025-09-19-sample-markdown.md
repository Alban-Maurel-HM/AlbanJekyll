---
layout: post
title: How I Counted Digimon
subtitle: And Created a Good 3 Digimon Team
cover-img: /assets/img/startCode.png
gh-repo: Alban-Maurel-HM/AlbanJekyll
gh-badge: [star, fork, follow]
tags: [digimon, team, speed]
comments: true
mathjax: true
author: Alban Maurel
---

What is the average speed of all digimon? How many digimon have a certain attribute? What is a possible team I can use? I was tasked with answering these questions as! Here are my answers: 


First, I used this code to find both the average speed and the amount of digimons with a certain attribute. 

```python
import csv
def count_digimon(column, specific): #count and speed avg
    with open("digimon.csv", "r") as f:
        reader = csv.DictReader(f) 
        speed = [] #list that I can later take average of
        count = 0 #amount with a "specific" attribute
        for row in reader:
            row["Spd"] = int(row["Spd"]) 
            speed.append(row["Spd"]) 
            if row[column] == specific:
              count += 1
        speed_avg = sum(speed)/len(speed)      
        print("The amount of digimon with", specific, "is", count) #nice formatting
        print("Avg speed is:", speed_avg)
count_digimon("Type", "Vaccine") #example given
```
Next, to find the team, I used a nested for loop with certain requirments in power and amount of memory. 

```python
def team(): #find team of 3
    with open("digimon.csv", "r") as f:
        team_reader = csv.DictReader(f)
        for a in team_reader:
            for b in team_reader:
                for c in team_reader:
                    if a["Number"] != b["Number"] != c["Number"]: #cannot be the same
                        if (int(a["Memory"]) + int(b["Memory"]) + 
                            int(c["Memory"])) < 16 and (int(a["Atk"]) 
                            + int(b["Atk"]) + int(c["Atk"])) > 299: #two needed
                            print("Your team can be:", a["Digimon"], b["Digimon"], c["Digimon"])
team()
```

The main struggle was staying organized while getting different information. Tracking several different things was not easy. My final team is: Kuramon Pabumon Ogremon, and the average speed is 120.40160642570281. 