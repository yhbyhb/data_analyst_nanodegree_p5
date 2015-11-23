Make Effective Data Visualization: Airline On-time Arrival Performance
========================================================
by HanByul Yang, November 18, 2015

## Summary ##
This charts shows on-time arrival performance of top 5 U.S. airlines for domestic flights and overall airline from 2003 to 2015. Top 5 airline cover over half of all flights. A flight is considered delayed when it arrived 15 or more minutes than the schedule. The [data set](http://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp) which contains information on United State flight delays and performance comes from BTS in OST-R.

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

When releasing initial chart, I used top 3 airlines results with no rational reason. There was some feedback point out "Why top 3 airelines?". With more data exploration, As above table, top 5 airlines covers half of all flights from 2003 to 2015. I decided to shows on-time performace trend of top 5 airlines with overall(28 airlines) on-time performance. It shows most of airlines performed poorly in 2007 and have pick in 2012. 

**On-time performance of top 5 airelines**
![initial plot with R](https://raw.githubusercontent.com/yhbyhb/data_analyst_nanodegree_p5/master/data/figure/top5_airlines_and_overall-1.png)

<!-- **On-time arrival performance**

Year | American Airlines Inc. | Delta Air Lines Inc. | ExpressJet Airlines Inc. | SkyWest Airlines Inc. | Southwest Airlines Co. | Overall
---|---:|---:|---:|---:|---:|---:
2003 | 0.8119 | 0.8231 | 0.8062 | 0.8898 | 0.8691 | 0.8286
2004 | 0.7879 | 0.7790 | 0.7888 | 0.8498 | 0.8126 | 0.8006
2005 | 0.7856 | 0.7917 | 0.7804 | 0.8448 | 0.8175 | 0.7947
2006 | 0.7738 | 0.7804 | 0.7592 | 0.7925 | 0.8121 | 0.7738
2007 | 0.7190 | 0.7848 | 0.7664 | 0.7819 | 0.8114 | 0.7580
2008 | 0.7305 | 0.7813 | 0.7653 | 0.8144 | 0.8171 | 0.7825
2009 | 0.7923 | 0.7992 | 0.8083 | 0.8378 | 0.8393 | 0.8111
2010 | 0.8168 | 0.7961 | 0.8015 | 0.8133 | 0.8068 | 0.8179
2011 | 0.8068 | 0.8388 | 0.7839 | 0.8175 | 0.8257 | 0.8176
2012 | 0.7910 | 0.8723 | 0.7920 | 0.8361 | 0.8413 | 0.8335
2013 | 0.7976 | 0.8501 | 0.7589 | 0.8214 | 0.7763 | 0.8007
2014 | 0.7773 | 0.8470 | 0.7603 | 0.7961 | 0.7453 | 0.7868
2015 | 0.8106 | 0.8580 | 0.8023 | 0.8162 | 0.8052 | 0.8094 -->

### Data Visualization ###
**dimple.js** is mainly used for making chart. **D3.js** also used.
I used line chart with scatter plot that indicates individual data points. Line chart is the best method to show changing values in time. Scatter plot emphasizes data points at each year. Each airlines performance is distinguished by coloring each line and points series.
The legend is placed bottom-right conrnor of the chart. X-axis is in range from 2003 to 2015 and formatted with Year. Percentile is used for unit of y-axis. The range of y-axis is decided with min value 0.7 and max value 0.9 in order to maximize the differences among airlines performace. I worried about lie factor by not setting min y value to 0.

The following chart is initial chart. It also can be found at `index-initial.html`.

![initial chart](https://raw.githubusercontent.com/yhbyhb/data_analyst_nanodegree_p5/master/data/figure/index-initial.png)

#### Final chart (after feedbacks) ####

## Feedback ##
### Feedback 1 ###
what "average" mean?  average of top3?
"on-time performance" ??
### Feedback 2 ###
hard to compare each line
range of y axis makes confuse
hovering tooltip looks good but no additional information.
### Feedback 3 ###
강조하고 싶은것이 있으면 더 좋겠다
목적이 좀 더 분명히 잘 보이면 좋겠다. 
70% 부터 있어서 잘 안보임. 
왜 세개? 오버올이 다른것들의 평균인줄알았음
최악의 항공사는?

## Resources ##
- dimple examples, docs
    - [Interactive Legend](http://dimplejs.org/advanced_examples_viewer.html?id=advanced_interactive_legends)
- d3 doc
- course materials