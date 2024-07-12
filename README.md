**3 Visualizations about Color Distribution on National Flags**

*Introduction*

I chose the data on national flags and their colors because flags are powerful symbols of identity, culture, and history. Each color on a flag often carries significant meaning, representing aspects such as freedom, peace, struggle, and heritage. A dataset on national flags and their included colors is intriguing because it allows for the exploration of the visual and symbolic elements that nations choose to represent themselves. By analyzing the colors of flags over time and across regions, we can gain insights into common themes and unique attributes that characterize different countries and historical periods.

*The Research Question*

How has the color distribution on national flags across different regions and time periods from 1874 to 2024 changed and are there meaningful conclusions as to why, how, and the underlying meaning to be derived from visualizing these changes?

*Building a dataset*

To gather this data, I scraped information from the website https://flaglog.com/historical. This user-run site provides a wide array of historical flags and their details, making it a useful source for our analysis. The data includes a whole lot of information on flags, the years they were adopted and retired, and the regions they represent. 

To scrape the data, I used the following Python libraries: `requests` for making HTTP requests, `BeautifulSoup` for parsing HTML content, and `PIL` for image processing. The process involved sending requests to the website for each year from 1874 to 2024, extracting relevant information about each flag, and analyzing the colors used in each flag image. The scraping code identified and downloaded flag images, categorized the colors, and calculated their proportions. Here is a brief overview of the scraping process:
1. Downloading Images: For each flag, the script downloaded the image using its URL. This involved sending an HTTP GET request and handling the response to retrieve the image content.
2. Color Analysis: The downloaded images were analyzed to determine the color composition. The script converted the image to RGB format and categorized each pixel into predefined color categories. It then calculated the percentage of each color in the image.
3. Data Storage: The extracted information, including image URL, region, state name, flag name, additional info, year added, year removed, and color percentages, was stored in a CSV file. This structured format makes it easy to analyze and visualize the data.
  
*Problems with my dataset*

Since my dataset source is a private user-run website that itself doesn't cite many sources, the accuracy of the data can be put into question. The website isn't officially curated or authoritative. It's contents might contain inaccuracies and should be interpreted with caution.

Additionally, the way I sorted the data to fit my agenda poses additional problems. Since my goal is to visualize changes in color on national flags and the goal of the original website is to display historical flags and sort them by regions, the websites layout wasn't setup with my goal in mind which lead to some unintended consequences. The regions the flags are sorted in change over time, depending on how relevant the region was at the time regarding flag usage. For example, Africa (which is actually only sub-saharan Africa) as a region only gets introduced in 1897, whereas before Africa and the Middle East where put in the same category (from 1897 and onwards, only North Africa and the Middle East are in the same category). Obviously, trying to visualoze color changes by region makes this difficult. Since this only affected Africa, Central Asia and the Carribean though, I decided it would be fine and wouldn't affect make my findings to a noticable degree.

There is also the problem of color definition. I defined in my code what "green" means, what any of my colors mean in regards to their combination of red, green and blue and then said, that every pixel should be sorted into either of my ten abitrarily picked colors. Who says every user using my visualizations understands "pink" or "turquoise" the same way I do? Maybe the visualization would look differently using their color definitions. It is a subjective categorization every user should be aware of.

Lastly, there's the problem of what even constitutes as a national flag. Is a merchant flag a national flag? How about contries in civil war with different parties claiming to be the "real" nation? What about religious groups claiming to be a nation? There's also indigenous tribes and people as well as indepedent regions or just countries with disputed recongition. I used every flag that the website used just to avoid having to go through every one and deciding whether to include it or not. Well, almost. I ignored every flag the website counted as "Other International and Cultural Flags" like the EU, Esperanto or Red Cross flags. The answer to whether or not those count as national flags was in my opinion pretty clear cut.

By acknowledging these limitations, I want to remind users that my visualizations serve as a starting point for deeper exploration rather than absolute truth. The data allows us to observe broad trends, such as the prevalence of certain colors in specific regions or periods, but the nuances and exceptions require careful consideration and further research.
  
*Visualization 1: Fun with flags*

This first visualization in a series of three focuses on the distribution of colors in national flags across various regions and from 1874 to 2024. It offers users an engaging interface to delve into the visual and symbolic language of flags, making it both educational, insightful and fun. It is by far the most complex of the three and should be seen as the focal point of this work.

It has four different capabilities to interact with it: Firstly, the region being observed can be decided by a drop-down menu. The standard option is worldwide. Secondly, the colors displayed in the pie chart can be disabled and enabled. The standard is every color being displayed. The third possible way to interact with the visualization is the timeline at the bottom. It allows in steps of ten to view single years as well as certain periods. Lastly, it's possible to view all included flags in a color by clicking on the relevant pie chart segment, sorted by the most area occupied by the relevant color. The standard option is that all flags are displayed at the bottom, sorted alphabetically.

Additionally, the visualization includes detailed tooltips that offer more information about each color and flag. When users hover over a pie chart segment, they see color-related details such as average area occupied by the color on all flags as well as only flags that include the clicked-on color and the amount of included flags. When users hover over a flag image displayed in the image contianer, they can see details such as the state name, flag name, the years the flag was in use, the percentage of each color in the flag as well as (if available) additional information and flag type. 

Regarding the additional libraries I used: Plotly Express is utilized to generate interactive pie charts that display the color distribution of national flags. Plotly simplifies the creation of visually appealing and interactive charts. To create the web application, the Dash framework is employed. Dash allows the development of interactive and data-driven web apps using Python. Within Dash, dcc (Dash Core Components) and html modules help design the dashboard layout, including dropdown menus, range sliders, and the arrangement of visual elements. The dash.dependencies module manages interactivity, using Input, Output, and State classes to define callbacks that update visualizations based on user interactions.

One of the key goals of this visualization is to make the data more accessible and engaging. By transforming a static dataset into an interactive tool, it encourages users to explore and discover patterns on their own. This interactivity not only makes the data more interesting but also helps users to better retain and understand the information.

It does have a flaw, though. Since some countries change their flag more than others, whenever a period is observed and visualized in the pie chart, some countries are inflating certain color representations. For example, over the entire 150 years, Albania changed it's flag nine times with only minimal changes. The pie chart treats these nine flags as distinct flags though, which is why in this example, red and black are slightly inflated. On the other hand, if i would only include the latest flag when looking at time period and displaying the changes in a pie chart, that would also not be representative and falsify the data. Maybe it isn't a flaw but a feature. A feature the user should be aware of anyway.

*Visualization 2: Plotting the changes*

The second visualization provides a dynamic and detailed look at the trends in flag colors over time, distinguishing itself from the previous visualization by focusing on temporal changes rather than just static distributions.

The core of this visualization is a line plot that shows the average percentage of each color used in flags from 1874 to 2024. Users can interact with the plot by selecting a specific region and optionally filtering by a particular color. This interactivity is facilitated through dropdown menus, allowing users to customize the view according to their interests.

matplotlib.pyplot is used to generate the line plots that show the percentage of each color on national flags over time. This library is well-suited for creating detailed and customizable static visualizations. ipywidgets enables the creation of interactive widgets in Jupyter notebooks. By using interact and widgets, users can select different regions and colors from dropdown menus.

It's particularly interesting because it allows users to see how the use of different colors in flags has evolved over time. By selecting different regions, users can compare trends across continents or specific geopolitical areas. For example, they can observe how the use of red in European flags might have spiked during certain historical periods or how green became more prominent in African flags post-colonialism.

The ability to filter by color adds another layer of depth to the analysis. Users can focus on a single color to see its trajectory across different years, helping to identify periods when that color became more or less popular. This can be linked to historical events, cultural shifts, or political changes. For instance, the rise in the use of red might correspond with periods of communist or socialist popularity on the world stage.

By using line plots, the visualization effectively communicates the trends and fluctuations in color usage. The aggregation of data by year and color provides a clear picture of the average percentage of each color used in flags for the selected region. This approach makes it easier to spot patterns and outliers, giving users valuable insights into the historical significance of colors in national flags.

*Visualization 3: A focus on region differences*

My last visualization is a heatmap showing the average percentage of a selected color in national flags by decade and region, providing a different perspective compared to the previous visualizations. This heatmap visualization is interesting because it allows users to see both temporal and regional variations in the use of specific colors, offering a comprehensive overview of how certain colors have been adopted or discarded over time and across different parts of the world.

The key feature of this visualization is its ability to present data in a matrix format, where each cell represents the average percentage of a specific color in flags for a particular region and decade. By selecting a color from a dropdown menu, users can highlight the prevalence of that color in different regions over time. This format makes it easy to identify patterns and anomalies, such as which regions predominantly use a certain color and how its usage has changed over the decades.

The seaborn library is central to this visualization, as it simplifies the process of creating informative and attractive statistical graphics. In this case, seaborn.heatmap is used to generate the heatmap, which provides a clear visual representation of how the usage of a specific color has changed over time across different regions.

The preparation of the heatmap data involves grouping the data by region and decade, then calculating the average percentage of the selected color for each combination. This aggregated data is then displayed in a heatmap using Seaborn, a powerful visualization library in Python. The heatmap is annotated with the exact percentage values, making it easy to read and interpret the data.

One of the main differences between this visualization and the previous ones is the way data is aggregated and presented. While the first visualization provided a snapshot of color distribution and the second showed temporal trends through line plots, this heatmap focuses on both temporal and regional distributions simultaneously. This dual focus allows users to see more granular patterns and correlations, such as how regional preferences for certain colors might align with historical events or cultural shifts.

*Conclusions*

While my first visualization puts an emphasis on exploration, fun and learning. Both the second and third visualizations make it easier to make observations on the changes over the 150 years covered. While these conclusions are not definitive, they are based on observed patterns and correlations that offer valuable perspectives. Here are my observations on all the colors in no particular order:

I see a correlation between maritime nations and usage of the color blue in their national flags. Both the Carribean and Oceania have blue as their most prominent color.

Green seems to be both very prominent on flags of countries with muslim belief like most of the Middle East and even South Asia (i.e. Pakistan). It seems also to be very prevalent on flags of nations that include a lot of jungles like in Central Africa and Latin America. Overall green's average area on flags grew over the 150 years. This can be attributed to the decolonisation of Africa.

On a worldwide scale, while still being the most popular color, we observe a decrease in red on national flags. This could be contributed to the decline or decrease in amount of socialist or communist nations. Both the end of World War Two and the fall of the Soviet Union can be seen on the second visualization, the latter being particularly apparent when focussing on Central Asia.

The color orange really can only be seen in South Asia. This may be contributed to Hindu belief the geographical concentration thereof.

Pink is the rarest color, only appearing on six flags with island nations making up most of them. I can't explain this phenomenon other than it's just a color that doesn't really match with a lot of others. It's definitely interesting though that we haven't really had a national flag include the color pink since 1947.

The color yellow was most popular in the late 19th and early 20th century. It never really was popular though. The sample size is pretty low and greatly inflates it's popularity. Still, it seems to decline with countries like Russia and China whose flags used to be yellow both moving away from it over time.

If there is a trend in popular colors to be called out, it may be turquoise. Only really appearing in the 1940s it has been growing in popularity across almost all regions ever since. I can't really put my finger on why. Like pink, in my opinion the color doesn't match all that well with others and unlike green (forests), blue (water) or yellow (sun) I don't know what the color is trying to represent.

White is probably the most consistent color of all, keeping it's average share on national flags whilst almost always keeping control of a considerable area across all regions and decades.

Black reached it's lowest point during the late 1940s. Although today the color is  most prevalent in arabic countries like Egypt or Iraq, 100 years ago black was most used on national flags in South and East Asia while the flags of countries in North Africa and the Middle East were almost only red in color. This probably represents some kind of identity shift I can't go into more detail about because of my lack of knowledge on the subject. The asian countries really lack in sample size to make accurate assessments in regards to trends or reasons as to why black was used and isn't anymore.

Lastly, violet or purple is now mostly used in flags of native american tribes and people. Another period in which violet so a lot of usage was the 19th century and earlier in South Asia. It seemed to have been a popular color for flags of hindu kingdoms of that time. Overall, there aren't really a lot of trends observable regarding violet. It always sat comfortably around 1.5 to 3 percent worldwide.

In conclusion, while the analysis of color distribution in national flags offers intriguing insights into how historical events and cultural shifts might have influenced national identities, it is crucial to approach these findings with a degree of skepticism. The visualizations provide a compelling narrative, but they are based on patterns and correlations that might or might not hold true upon closer examination. These conclusions serve as a starting point for deeper exploration rather than definitive answers.
