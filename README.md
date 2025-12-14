# MLB-Analytics-Revolution
Editor's Note: Adding a blog style notes to this analysis in README until I have something else set up.  
All data gathered from Baseball Reference.  

### Foreword  
This analysis was originally completed and taught in a 2023 Statistical Consulting class at MIT. The legendary MIT statistician [Arnie Barnett](https://mitsloan.mit.edu/faculty/directory/arnold-i-barnett) usually taught the class while I was his lowly TA. Knowing I was enamored with sports analytics and statistics, Arnie encouraged me to teach a class on the subject and the main findings of the analysis are in this repo. The lecture was more narrative-driven and less statistics.  

The analysis in this repo was updated based on the last three seasons of the MLB.

### Introduction  
The initial goal was simple: understand what team stat gave the best indication of a baseball team's offensive success. Offesnive success is measured in runs scored, not number of team wins. Although more runs naturally leads to more wins, offensive stats are entirely dependent on runs against. "Entirely dependent" may be hasty; a monster offensive output could have a negative mental toll on the opposing team's offensive performance. This dependency was not tested. Instead, I individually looked at Offensive Stats as a function of runs scored and Pitching Stats as a function of runs against.

### Hitting Stats Overview  
I compared six hitting statistics: Home Runs (HR), Batting Average (BA), On-base Percentage (OBP), Slugging Percentage (SLG), On-base plus Slugging Percentage (OPS), On-base plus Slugging Percentage Plus (OPS+). The expectation and results indicate that all six statistics have a positive correlation with runs scored. I wanted to test which is the most positively correlated with runs scored.  

The below table summarizes the results per year:  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/'23%20to%20'25%20hitting%20stats%20summary.png" alt="2023 to 2025 Hitting Stat Summaries" width="333" height="333">

Some high level takeaways:  
-Batting average is truly an overrated stat. It was much lower performing than all stats but home runs. (JT Note: Could I do the same analysis for an older year?)  
-OPS reigns supreme. It also has the least amount of general variance in importance year-over-year. If your team does both get on base and hit for power well, you will score a lot of runs. Duh.  
-Why did every stat perform significantly worse in 2025?  
-OPS+ performs worse than just regular OPS. More like OPS- amirite hahaha. More exploration on OPS+ below.

### OPS+ Exploration  
Some context on OPS+ per [Fangraphs](https://library.fangraphs.com/offense/ops/):  

*This statistic normalizes a player’s OPS — it adjusts for small variables that might affect OPS scores (e.g. park effects) and puts the statistic on an easy-to-understand scale. A 100 OPS+ is league average, and each point up or down is one percentage  point above or below league average.  In other words, if a player had a 90 OPS+ last season, that means their OPS was 10% below league average.*  

Based on the definition of OPS+, it seems better to use it as a player comparison metric rather than a team comparison. I still wonder why OPS+ performs worse than Slugging Percentage as a metric that indicates run scoring success. My initial thoughts center on OPS+ being more dependent on things like park effects as FanGraphs notes. For instance, if a team plays home games in a hitter friendly park, that could lead to an artificially inflated SLG and OPS, but OPS+ should normalize it.  

When diving into team OPS and OPS+ in 2025, I immediately noticed the Texas Rangers. They had an exact league average 100 OPS+ which indicated being 14th overall in OPS+ rankings among teams. Meanwhile, their OPS was 0.684 compared to a 0.719 league average slotting them into 26th in team rankings for OPS. Based on my prediction from the last paragraph, I would expect the Rangers to play in a pitching friendly park meaning that OPS could be artificially deflated because of park logistics. The below table also lists the Rangers OPS and OPS+ rankings:  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/Rangers.png" alt="Rangers OPS vs OPS+" width="333" height="400">  

My prediction seems to be spot on. Per [Baseball Savant’s Park Factor](https://baseballsavant.mlb.com/leaderboard/statcast-park-factors) stat, the Rangers play in the second most pitcher-friendly stadium, only behind the Seattle Mariners. To take this a step further, let’s also compare the Mariners’ ranking and take the most hitter-friendly park (Colorado’s Coors Field) and see if we have similar expected OPS and OPS+ discrepancies for these teams.  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/Mariners%20and%20Rockies.png" alt="Mariners and Rockies OPS vs OPS+" width="333" height="400">  

Spot on. Every year indicates that the Rockies slug higher than they objectively should and the opposite for the Mariners.  

Overall, statistics show that OPS is much better than OPS+ at predicting how many runs a team will score compared to other teams. But OPS+ is a much more objective stat that seeks to rank teams based on their performance in a vacuum. Regardless, I think both are much better indicators and serve a better purpose to the baseball statistician than the traditional batting average.  

### Exploring a Weighted On-Base Statistic  

As we pull the thread further on trying to find the ideal team stat to indicate offensive output, a 2010 [FanGraphs](https://library.fangraphs.com/offense/ops/) blog post suggested looking further into weighted on-base average (wOBA):  

*If you have the choice, use Weighted On-Base Average (wOBA) instead of OPS. OPS weighs both OBP and SLG the same, while wOBA accounts for the fact that OBP is actually more valuable.*  

First, let’s rediscover if the claim on OBP being more valuable holds true by doing a simple R-squared comparison of the 2023-2025 data I analyzed.  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/OBP%20vs%20SLG.png" alt="Isolating OBP vs SLG" width="333" height="333">  

OBP outperformed SLG in two of three seasons using my simplified approach to testing their overall importance. My suspicion is that OBP is still more important overall but different factors can contribute to more success year-over-year. For instance, the 2023 season was the first season where many new rules were implemented to speed up the game, most notably the introduction of a pitch clock. Introducing this could have led to pitchers working faster than they were previously used to and giving up hits leading to a greater SLG. This is explored more in the concluding section.  

To wrap up the analysis, I took a version of wOBA, Baseball Reference’s rOBA, and created the same charts as the other offensive statistics. As shown in the graph and table below, rOBA was the best indicator of Runs Scored of any of the hitting statistics in only 2024 and 2025. Was the weighting of rOBA in 2023 upended due to SLG having a greater impact on run scoring that season?  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/rOBA%20Stats.png" alt="rOBA Trends per Year" width="500" height="333">  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/Adding%20rOBA.png" alt="Adding rOBA to Summary Statistics" width="333" height="333">  

### Conclusion and Final Questions  

*Can changes in gameplay alter a statistic’s significance?*  

The 2023 MLB season saw significant changes in gameplay rules with the banning of defensive shifts and the introduction of the pitch clock. How did this contribute to how we view some of these hitting statistics? Let’s start simple:  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/Basic%202022%20and%202023%20Stats.png" alt="Simple 2022-2023 Stats" width="333" height="333">  

We immediately see a more significant number of home runs in 2023 compared to 2022. This potentially adds ammo to my hypothesis that pitchers needed more time to adjust to the pitch clock, but not claiming any causal inferences. A greater percent increase in home runs compared to runs could also lead to SLG purely being more impactful than OBP for this 2023 season.  

To answer the question that started this section: yes, changes in gameplay and rules will alter statistics because a team’s strategy will entirely change. If the NBA ever [removes the corner 3 point shot](https://www.youtube.com/watch?v=_YMQRVzCoN8) from the game, I would expect a similar year where typical statistical predictions are harder to utilize.  

*Why did all of the stats I studied in 2025 have worse performance than the other years?*  

Essentially all statistics in 2025 showed worse performances than other years with the exception of OPS+ in 2024. Are there any immediate trends of beliefs that could explain this?  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/2025%20Outliers.png" alt="2025 Outliers" width="500" height="450"> 

If we keep this as simple as possible, we can see that Runs and Home Run total were, more or less, the same in all three years. However, individual players were hitting into more outs with Double Plays and Strikeouts both at their lowest in this three year period. So, how can we try to make sense of less predictable stats in 2025? I thought a collective lack or boom of clutch hitting could lead to less predictability but OBS with runners in scoring position generally stayed the same.  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/GIDP%20and%20K's.png" alt="GIDP and K Data" width="333" height="333">  

Could there be a sample space issue with a few teams just immediately breaking the trendline? Let’s bring in the 2025 plots:  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/More%20Basic%20Stats.png" alt="More Basic Stats per Year" width="333" height="333">  

There are a couple of huge outlier culprits that I want to take out, one that scored more runs than expected and one that scored less: Milwaukee Brewers and the Colorado Rockies, respectively. How much better do the summary statistics look without these two teams in the analysis?  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/Without%20MIL%20and%20COR.png" alt="Data without MIL and COR" width="333" height="333">  

Overall, the statistics are not that much better. Some perform better, some do not. For this simple exercise, I’m chalking the 2025 season to a shrug shoulders and move on!  
