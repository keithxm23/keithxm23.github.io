---
layout: post
title:  "Oddities this season"
date:   2016-01-10 21:40:01
categories: epl d3
extra_css:
  - odds.css
extra_js:
  - https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.12/d3.min.js
  - /js/odds.js
---
Hover over (or if you're on mobile, click) the bars to view the relevant match details.
<script type="text/javascript">
  //Load from CSV File
  // d3.csv("odds_beaten.csv", render);
  //OR
  //Load from embedded csv in html
  window.onload = function() {
    var raw = d3.select("#csvdata").text();
    var parsedOddsData = d3.csv.parse(raw);
    render(parsedOddsData, "#svgPlaceholder");
  };
</script>
<!-- Div to be used for tooltip -->
<div id="tooltip" class="hidden">
    <table id="value">
    </table>
</div>
<pre id="csvdata">
team,oddities,points,l2w,l2d,w2d,w2l
Arsenal,6,42,0,0,3,3
Leicester,12,40,5,5,2,0
"Man City",7,39,0,1,2,4
Tottenham,12,36,2,3,6,1
"Man United",10,33,0,0,6,4
"West Ham",17,32,7,3,5,2
"Crystal Palace",11,31,5,3,1,2
Liverpool,13,30,2,3,3,5
Watford,10,29,4,4,1,1
Stoke,16,29,7,4,1,4
Everton,13,27,2,4,5,2
"West Brom",10,26,4,5,0,1
Southampton,13,24,2,1,5,5
Chelsea,13,23,0,2,3,8
Norwich,11,23,3,4,1,3
Bournemouth,12,21,4,3,3,2
Swansea,10,19,1,2,5,2
Newcastle,9,17,3,3,2,1
Sunderland,6,15,2,3,0,1
"Aston Villa",9,8,1,3,2,3</pre>

<div id="svgPlaceholder">
</div>

#Some analysis
The 'predicted' result is simply the result that had the best odds. An interesting observation was that bookmakers rarely (or in this case, never) gave the best odds for a draw result. There's a fascinating science
behind this, but that is outside the scope of this post.

I thought it was interesting how the bar-heights almost define a bell curve. There were
fewer unexpected results for teams at the top (Arsenal, City) and the bottom of
the table (Sunderland, Villa) because they either consistently won or lost their
games as expected. Meanwhile, it's been difficult predicting results for the
mid-table teams.

West Ham and Stoke are like wildcard giant-killer teams this season. West Ham
managed to defeat Arsenal, City, Chelsea, Liverpool and drew with United. Stoke
stole points from Chelsea, City, United and Spurs. However both teams dropped
points against oppositions you would've expected them to beat which is why they
aren't doing as well as the high-flying Leicester this season.

Also worth noting is the stark contrast in Leicester's and Chelsea's seasons.
The Foxes had 10 unexpectedly positive results in their favor whereas Chelsea dropped points on 11 unexpected occasions.



#Work
I've been teaching myself [D3.js] and thought this would be an interesting project
to try out. The data is from [football-data.co.uk] which includes match results and betting odds.
I normalized the data available to make it much easier to query as part of [this project]. You can download the matchdb.db database (sqlite3) and run queries of your own. The database includes match data for seasons 2003-04 to present and also the otherwise missing referee data for the 2012-13 season and some corrected referee data.
Feel free to fork the project or submit pull requests if you can think of ways of improving the parsing script. Heads up, it was written over a weekend and doesn't follow a lot of Python standards (as with all quick'n'dirty scripts) but I'll get to that eventually.

Lastly, shameless plug for my Fantasy website, [FPL Assistant], which you might find interesting if you play the [Fantasy Premier League].

[D3.js]: http://d3js.org/
[football-data.co.uk]: http://www.football-data.co.uk/englandm.php
[this project]: https://github.com/keithxm23/football-data-analysis
[FPL Assistant]: http://www.fplassistant.com/
[Fantasy Premier League]: http://fantasy.premierleague.com/
