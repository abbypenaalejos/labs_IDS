This application is in support of the article in _Urban Studies_, ["Locating neighborhood diversity in the American Metropolis."](http://usj.sagepub.com/content/early/2016/04/29/0042098016643481.abstract)  The article analyzes geographic variations in neighborhood racial and ethnic diversity over time in large metropolitan areas in the United States.  As of August 2022, this application is updated with data from the 2020 Decennial US Census.  All data are standardized to 2010 Census tracts thanks to NHGIS.  

The key metric in this article is the neighborhood-level _entropy index_ (called "diversity score" in the application), which measures the degree of neighborhood diversity for six general racial/ethnic groups: non-Hispanic white, non-Hispanic black, Hispanic, Asian/Pacific Islander, Native American.  The entropy index $E$ is calculated as follows (Farrell and Lee 2011):  

$$E = {\sum\limits_{r=1}^{n}Q_r}ln{\dfrac{1}{Q_r}}$$

where $Q_r$ is group $r$'s proportion of the neighborhood population.  The maximum value of $E$, then, is the natural log of the number of groups - which would occur when all groups in a neighborhood are of equal size. Following [Hall and Lee (2010)](http://usj.sagepub.com/content/47/1/3.abstract), [Farrell and Lee (2011)](http://www.sciencedirect.com/science/article/pii/S0049089X11000706), and [Wright et al. (2014)](http://www.tandfonline.com/doi/abs/10.1080/00330124.2012.735924#.Vwxi7fkrLRY), $E$ is scaled by its maximum by dividing by $ln(6)$, setting the range of values from 0 to 1.  

To study how neighborhood diversity varies with distance from urban cores in the largest metropolitan areas in the United States, entropy indices are plotted against the distance from the Census tract centroids to their corresponding nearest major city hall.  Locally-weighted regression (LOESS) is then used to produce a "diversity gradient" of estimates of neighborhood diversity by distance from the city center.  

This application allows visitors to explore this part of the paper interactively.  The article follows by using local exploratory spatial data analysis techniques to identify how spatial clusters of diversity have shifted over time; this will be the focus of a future application that corresponds to an extension of the study published in _Urban Studies._  

Demographic data come from [the National Historical Geographic Information System](https://www.nhgis.org/)'s Time Series tables, which standardize decennial Census data from 1990 through 2020 to 2010 Census tracts.  Geographic data in the application are from the [US Census Bureau's Cartographic Boundary Files](https://www.census.gov/geo/maps-data/data/tiger-cart-boundary.html), obtained with the [R tigris package](https://walker-data.com/census-r/census-geographic-data-and-applications-in-r.html). Entropy indices are built with the [R segregation package](https://elbersb.github.io/segregation/index.html).  

The application is built with the [Shiny](http://shiny.rstudio.com) framework for the [R programming language](https://www.r-project.org/). The application layout is produced with the [flexdashboard](http://rstudio.github.io/flexdashboard/index.html) package, and the charts and maps use [Plotly](http://plot.ly), [Leaflet.js](http://leafletjs.com/), [Highcharts](http://www.highcharts.com/), and [ggplot2](http://ggplot2.org/), all accessed through their corresponding R packages.  Code for the application is available at <https://github.com/walkerke/neighborhood_diversity>.  

To learn more about my work, [visit my website](https://walker-data.com) or [connect with me on Twitter](https://twitter.com/kyle_e_walker).  