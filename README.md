# Tableau
**Current Problem and Business Case**

The current strategy for data management concerning vendor relationships is, by
running SQL query, to collect the corresponding vendor’s name and company, team
leader’s name and supervisor’s name. Then, some statistics, such as how many
vendors under a supervisor would be drawn from the collected data. However, this
kind of solution cannot sketch the panorama of the vendor relationships.
Therefore, I, assisted by Tableau and R, made efforts in visualizing the vendor
relationship.

**Method: Visualization with Tableau**

The Tableau does not have templates for the organizational chart. Hence, I
conducted some researches and found a solution developed by Josh Weyburne . I
will briefly introduce the method below:

1.  Wrangled the data set to create a two-column data frame that described all
    the relationships among these people and company.

2.  Used the self-join and union operation in Tableau to extract the supervisor
    nodes level by level, determined the Y positions, and marked lines to draw.

3.  Used the first character of each word to create an Alphabetic order for each
    node, and thus to determine the X positions.

4.  Created a combined field for each node and its Y position. And then drew the
    lines to make the organizational chart.

**Organizational Chart Demo (Tableau)**

<img width=250px height=300px src="https://github.com/yipinlyu/Tableau/blob/master/demo.png"></img> 
<img width=250px height=300px src="https://github.com/yipinlyu/Tableau/blob/master/demo2.png"></img> 
<img width=250px height=300px src="https://github.com/yipinlyu/Tableau/blob/master/demo3.png"></img> 


Because of the privacy concern, I am not likely to show the detailed figures
that contain the full names of vendors, team leaders and supervisors. Hence, as
Fig. 1 indicates, I created a demo of a five-level organizational chart to
present the result. The left figure shows the overall organizational chart for
both a and b. The middle and the right figures illustrate the filtered
organizational chart for a and b. These figures look good and can be updated in
real-time, because I can connect the Tableau to the IBM DB2 Warehouse database
by using the SQL query.

However, we can find the main weakness of this method in Fig. 1. The node d has
two supervisor nodes, which means that some nodes under d’s management work for
a, and some for b. But the middle and the right graphs present all the nodes
under d’s management. The reason is that when I processed the input dataset, I
just kept the relationships between two neighbor levels, to generate the input
which is required by this method. In the real dataset, one company might be
managed by multiple team leaders. Therefore, we cannot use Tableau to draw an
organizational chart if there exist multiple-to-multiple relationships.  
However, the time spent on Tableau is still worthy. From this process, I got to
understand the advanced techniques in Tableau, such as how to conduct self-join
and union operations, create customized calculated field, and customize X and Y
positions for customized graphs. I also came to be aware of the limitations of
Tableau. The coding functions in Tableau cannot support data wangling
operations, such as the append and the split. Hence, it is not appropriate for
us to conduct complicated data wrangling in Tableau. We need to use SQL, R or
Python to preprocess the dataset in advance. Tableau is very powerful when it
has the template that you want.

**Reference**

[1] 	Weyburne, J. (2017, February 27). Building an Organizational Chart in Tableau. Retrieved from https://www.dataplusscience.com/SimpleOrgChart.html.
