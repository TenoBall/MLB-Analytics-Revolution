# MLB-Analytics-Revolution
Editor's Note: Adding a blog style notes to this analysis in README until I have something else set up.  
All data gathered from Baseball Reference.  

### Foreward  
This analysis was originally completed and taught in a 2023 Statistical Consulting class at MIT. The legendary MIT statistician [Arnie Barnett](https://mitsloan.mit.edu/faculty/directory/arnold-i-barnett) usually taught the class while I was his lowly TA. Knowing I was enamored with sports analytics and statistics, Arnie encouraged me to teach a class on the subject and the main findings of the analysis are in this repo. The lecture was more narrative-driven and less statistics.  

The analysis in this repo was updated based on the last three seasons of the MLB.

### Introduction  
The initial goal was simple: understand what team stat gave the best indication of a baseball team's offensive success. Offesnive success is measured in runs scored, not number of team wins. Although more runs naturally leads to more wins, offensive stats are entirely dependent on runs against. "Entirely dependent" may be hasty; a monster offensive output could have a negative mental toll on the opposing team's offensive performance. This dependency was not tested. Instead, I individually looked at Offensive Stats as a function of runs scored and Pitching Stats as a function of runs against.

### Hitting Stats Overview  
I compared six hitting statistics: Home Runs (HR), Batting Average (BA), On-base Percentage (OBP), Slugging Percentage (SLG), On-base plus Slugging Percentage (OPS), On-base plus Slugging Percentage Plus (OPS+). The expectation and results indicate that all six statistics have a positive correlation with runs scored. I wanted to test which is the most positively correlated with runs scored.  

The below table summarizes the results per year:  

<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/'23%20to%20'25%20hitting%20stats%20summary.png" alt="2023 to 2025 Hitting Stat Summaries" width="700" height="700">

Some high level takeaways:  
-Batting average is truly an overrated stat. It was much lower performing than all stats but home runs. (JT Note: Could I do the same analysis for an older year?)  
-OPS reigns supreme. It also has the least amount of general variance in importance year-over-year. If your team does both get on base and hit for power well, you will score a lot of runs. Duh.  
-Why did every stat perform significantly worse in 2025?
-OPS+ performs worse than just regular OPS. More like OPS- amirite hahaha. More exploration on OPS+ below.

### Why does OPS+ exist?  
Before 

### Appendix

2025 hitting stats vs runs scored:  
<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/2025%20MLB%20Runs%20Scored%20Plots.png" alt="2025 Hitting Stats vs Runs Scored" width="700" height="700">

2024 hitting stats vs runs scored:  
<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/2024%20MLB%20Runs%20Scored%20Plots.png" alt="2024 Hitting Stats vs Runs Scored" width="700" height="700">

2023 hitting stats vs runs scored:  
<img src="https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/2023%20MLB%20Runs%20Scored%20Plots.png" alt="2023 Hitting Stats vs Runs Scored" width="700" height="700">




### Pitching Stats  
2025 pitching stats vs runs allowed:  
![2025 Hitting Stats vs Runs Scored](https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/2025%20MLB%20Runs%20Allowed%20Plots.png)

2024 pitching stats vs runs allowed:  
![2024 Hitting Stats vs Runs Scored](https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/2024%20MLB%20Runs%20Allowed%20Plots.png)

2023 pitching stats vs runs allowed:  
![2023 Hitting Stats vs Runs Scored](https://github.com/TenoBall/MLB-Analytics-Revolution/blob/main/2023%20MLB%20Runs%20Allowed%20Plots.png)

### Why does ERA+ exist?
