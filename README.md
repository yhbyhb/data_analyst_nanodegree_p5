Make Effective Data Visualization: Airline On-time Arrival Performance
========================================================
by HanByul Yang, November 24, 2015

## Summary ##
This charts shows on-time arrival performance of top 5 U.S. airlines for domestic flights and overall airline from 2003 to 2015. Top 5 airline cover over half of all flights. A flight is considered delayed when it arrived 15 or more minutes than the schedule. On-time performance changes small in the vicinity of 80%.

## Design ##
### Data Exploration ###
I selected the Flights [data set](http://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp) which contains information on United State flight delays and performance. It comes from BTS(Bureau of Transportation Statistics) in OST-R(The Office of the Assistant Secretary for Research and Technology) which includes RITA(the Research and Innovative Technology Administration).

Data exploration was done with R Studio. For the details, please check the `data\dataExploration.html` and `data\dataExploration.Rmd`. At First, I tried to visualize yearly averaged on-time performace trend which contains on-time, delayed, cancelled and diverted flights percentage. But It showed not enough interesting information to me.

**On-time performance**
![average on-time performance](https://raw.githubusercontent.com/yhbyhb/data_analyst_nanodegree_p5/master/data/figure/on_time_performance_yearly-1.png)

There are 28 airlines in the datasets. I assumed there are some dominant airlines that operate most of flights. After aggregating gross flights by airlines, sort them with descending orders. results are as following:

**Top 5 Airline for domestic flights**

|  | Carrier name | flights / month | flights | cumulative flights | relative cumulative flights
|---:|---|---:|---:|---:|---:
|1 |   Southwest Airlines Co. | 1066402.4 | 13863231 | 13863231 | 0.1704143
|2 |     Delta Air Lines Inc. |  615297.0 |  7998861 | 21862092 | 0.2687406
|3 |   American Airlines Inc. |  570689.9 |  7418969 | 29281061 | 0.3599385
|4 |    SkyWest Airlines Inc. |  536215.5 |  6970802 | 36251863 | 0.4456273
|5 | ExpressJet Airlines Inc. |  457366.9 |  5945770 | 42197633 | 0.5187159
|  | Overall                  |  281947.3 |  2905363 |          |

When I drew initial chart, I used top 3 airlines results with no rational reason. There was some feedback point out "Why top 3 airelines?". With more data exploration, As above table, top 5 airlines covers half of all flights from 2003 to 2015. So I decided to shows on-time performace trend of top 5 airlines with overall(28 airlines) on-time performance. It shows most of airlines performed poorly in 2007 and have pick in 2012. 

**On-time performance of top 5 airelines**
![initial R plot](https://raw.githubusercontent.com/yhbyhb/data_analyst_nanodegree_p5/master/data/figure/top5_airlines_and_overall-1.png)

### Data Visualization ###
**dimple.js** is mainly used for making chart. **D3.js** also used.
I used line chart with scatter plot that indicates individual data points. Line chart is the best method to show changing values in time. Scatter plot emphasizes data points at each year. Each performance of airline is distinguished by coloring each line and point series.
The legend is placed at bottom-right conrnor of the chart. X-axis is in range from 2003 to 2015 and formatted with Year. Percentile that represent on-time performance is used for unit of y-axis. Although I worried about lie factor by not setting min y value to 0, The range of y-axis is decided with min value 0.7 and max value 0.9 in order to maximize the differences among airlines performace.

The following chart is initial chart. It also can be found at `index-initial.html`.

![initial chart](https://raw.githubusercontent.com/yhbyhb/data_analyst_nanodegree_p5/master/data/figure/index-initial.png)

#### Final chart (after feedbacks) ####
Followings are changes from initial chart.
- Refined title for showing the purpose of chart clearly.
- Added a label for explanation of delayed flight at bottom of the chart.
- Added click interaction on legend to show and hide each airline graph.
- Changed color of overall graph to grey for differentiating to other graph.
- Refined "Average" legend to "Overall (all 28 airlines)" for clear understanding.
- Changed position of legend from bottom of chart to near the lines.
- Changed range of y-axis to show 0 ~ 100% to remove lie factor.

Some feedbacks were not used for refining chart. I didn't use all 28 airlines data. Because it didn't give any information but confusion. Also I didn't use worst on-time performance airline data. I think It is enoungh to show top 5 airlines performances that covers 50% of all flights. I didn't give any additional information to hovering tooltip because I'd like to give only values of x and y-axis. To give additional info may disturb on main purpose of chart.

I intened to find trend of on-time arrival performance for helping on choice of airline. Below is a screenshot of my final visualization.
![final chart](https://raw.githubusercontent.com/yhbyhb/data_analyst_nanodegree_p5/master/data/figure/index-final.png)

## Feedback ##
I had 3 feedbacks from my friends who are not familiar with dataset. In case of feedback 1 and 2, I showed the chart without any explanations firstly and explained the chart and dataset after several minutes. On the other hand, feedback 3 is taken by providing both chart and explanation.

### Feedback 1 ###
- what does "average" mean? average of top3?
- what is "on-time performance"?
- It seems most airlines have almost same on-time performace.

### Feedback 2 ###
- What is main purpose of this chart?
- Why did you choose top 3 airlines?
- Min value of y-axis make me confused.
- Why don't you show the worst performance airline?
- What about plot all 28 airlines?

### Feedback 3 ###
- Hard to compare each line.
- Range of y axis makes confuse. (min of y-axis 70%)
- Hovering tooltip looks good but no additional information.

## Resources ##
- [dimple.js](http://dimplejs.org/) examples, docs
    - [Interactive Legend](http://dimplejs.org/advanced_examples_viewer.html?id=advanced_interactive_legends)
- [d3.js](http://d3js.org/) doc
- course materials