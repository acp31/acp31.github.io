---
layout: post
title:  Making a Responsive Trendline in D3
date:   2015-11-14
categories: Projects
---

I know it has been a while since I made my last post. I decided that I would only post if it was 
worth while because I felt it was not worth the time investment to give a weekly status update post.
Well now I have something to post about! Recently I was working as Front End engineer on "Should I 
Watch This" which is a web based application that displays graphed data of the quality of a
Television show over the life of the show. In this project I was responsible for making the trend 
visualizations and I also did all of the Angular Routing. But that is not why I am making this post. 
I ran into trouble when trying to make the Data vializations because I realized that D3.js does not 
contain anyway to make a trendline in D3. So i was tasked with creating one from scratch.


{% highlight javascript %}
var x1 = 0;
    var y1 = 0;
    var x2 = 0;
    var y2 = 0;
    var len = episodedataset.length;

    each(episodedataset, function(item, index) {
      x1 += item[0];
    });

    each(episodedataset, function(item, index) {
      y1 += item[1];
    });

    each(episodedataset, function(item, index) {
      x2 += (item[0] * item[1]);
    });

    each(episodedataset, function(item, index) {
      y2 += (item[0] * item[0]);
    });

    var slope = (((len * x2) - (x1 * y1)) / ((len * y2) - (x1 * x1)))
    var intercept = ((y1 - (slope * x1)) / len)
    var xLabels = episodedataset.map(function(d) {
      return d[0];
    });
    var xSeries = d3.range(1, xLabels.length + 1);
    var ySeries = episodedataset.map(function(d) {
      return d[1];
    });
    var a1 = xLabels[0];
    var b1 = slope + intercept;
    var a2 = xLabels[xLabels.length - 1];
    var b2 = slope * xSeries.length + intercept;
    var trendData = [
      [a1, b1, a2, b2]
    ];
    var trendLine = svg.select()
    var trendline = svg.selectAll(".trendline")
      .data(trendData);

    trendline.enter()
      .append("line")
      .attr("class", "trendline")
      .attr("x1", function(d) {
        return xScale(d[0]);
      })
      .attr("y1", function(d) {
        return yScale(d[1]);
      })
      .attr("x2", function(d) {
        return xScale(d[2]);
      })
      .attr("y2", function(d) {
        return yScale(d[3]);
      })
      .style("stroke", "rgb(197,197,199)")   
{% endhighlight %}

The each in the code is the underscore each fucntion that iterates over each item in a dataset. 
When you try and calculate a trednline there are basic statistical calculations that have to be 
done first. After that you need to calculate the slope and inercept. The a1, a2, a3, a4 are put 
through the x and y scales to be strechted over the graph. 


