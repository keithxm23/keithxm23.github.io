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

I've been teaching myself [D3.js] and thought this would be an interesting project
to try out. The data is from [football-data.co.uk] which includes match results and betting odds. The 'predicted' result is simply the result that
had the best odds. An interesting observation was that bookmakers rarely (or in this case, never) provide the best odds for a draw result. There's a really interesting science
behind this, but that is outside the scope of this post.



[D3.js]:       http://d3js.org/
[football-data.co.uk]: http://www.football-data.co.uk/englandm.php
