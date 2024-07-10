**3 Visualizations about Color Distribution on National Flags**

*Introduction*

I chose the data on national flags and their colors because flags are powerful symbols of identity, culture, and history. Each color on a flag often carries significant meaning, representing aspects such as freedom, peace, struggle, and heritage. A dataset on national flags and their included colors is intriguing because it allows for the exploration of the visual and symbolic elements that nations choose to represent themselves. By analyzing the colors of flags over time and across regions, we can gain insights into common themes and unique attributes that characterize different countries and historical periods.

*Building a dataset*

To gather this data, I scraped information from the website https://flaglog.com/historical. This user-run site provides a wide array of historical flags and their details, making it a useful source for our analysis. The data includes a whole lot of information on flags, the years they were adopted and retired, and the regions they represent. However, it is important to note that the website isn't necessarily officially curated or authoritative. This means that while the data provides a broad overview, it might contain inaccuracies and should be interpreted with caution.

Using data from a site like Flag Log has its pros and cons. While it offers a comprehensive collection of historical flags, it may also include inaccuracies and the site like any comprehensive list on stuff like this falls victim to fuzzy definitions of what constitutes a nation or national flag. This variability underscores the need to view our findings as indicative rather than conclusive.

By acknowledging these limitations, we remind users that our visualizations serve as a starting point for deeper exploration rather than absolute truth. The data allows us to observe broad trends, such as the prevalence of certain colors in specific regions or periods, but the nuances and exceptions require careful consideration and further research.

To scrape the data, I used the following Python libraries: `requests` for making HTTP requests, `BeautifulSoup` for parsing HTML content, and `PIL` for image processing. The process involved sending requests to the website for each year from 1874 to 2024, extracting relevant information about each flag, and analyzing the colors used in each flag image. The scraping code identified and downloaded flag images, categorized the colors, and calculated their proportions. Here is a brief overview of the scraping process:
1. Downloading Images: For each flag, the script downloaded the image using its URL. This involved sending an HTTP GET request and handling the response to retrieve the image content.
2. Color Analysis: The downloaded images were analyzed to determine the color composition. The script converted the image to RGB format and categorized each pixel into predefined color categories. It then calculated the percentage of each color in the image.
3. 3. Data Storage: The extracted information, including image URL, region, state name, flag name, additional info, year added, year removed, and color percentages, was stored in a CSV file. This structured format makes it easy to analyze and visualize the data.
  
*Visualization 1: Fun with flags*

This first visualization in a series of three focuses on the distribution of colors in national flags across various regions and from 1874 to 2024. It offers users an engaging interface to delve into the visual and symbolic language of flags, making it both educational, insightful and fun. It is by far the most complex of the three and should be seen as the focal point of this work.

Additionally, the visualization includes detailed tooltips that offer more information about each color and flag. When users hover over a flag image, they can see details such as the state name, flag name, the years the flag was in use, the percentage of each color in the flag as well as additional information and flag type. 

One of the key goals of this visualization is to make the data more accessible and engaging. By transforming a static dataset into an interactive tool, it encourages users to explore and discover patterns on their own. This interactivity not only makes the data more interesting but also helps users to better retain and understand the information.

*Visualization 2: Plotting the changes*

The second visualization provides a dynamic and detailed look at the trends in flag colors over time, distinguishing itself from the previous visualization by focusing on temporal changes rather than just static distributions.

The core of this visualization is a line plot that shows the average percentage of each color used in flags from 1874 to 2024. Users can interact with the plot by selecting a specific region and optionally filtering by a particular color. This interactivity is facilitated through dropdown menus, allowing users to customize the view according to their interests.

It's particularly interesting because it allows users to see how the use of different colors in flags has evolved over time. By selecting different regions, users can compare trends across continents or specific geopolitical areas. For example, they can observe how the use of red in European flags might have spiked during certain historical periods or how green became more prominent in African flags post-colonialism.

The ability to filter by color adds another layer of depth to the analysis. Users can focus on a single color to see its trajectory across different years, helping to identify periods when that color became more or less popular. This can be linked to historical events, cultural shifts, or political changes. For instance, the rise in the use of blue might correspond with periods of political unity or the adoption of certain ideologies.

By using line plots, the visualization effectively communicates the trends and fluctuations in color usage. The aggregation of data by year and color provides a clear picture of the average percentage of each color used in flags for the selected region. This approach makes it easier to spot patterns and outliers, giving users valuable insights into the historical significance of colors in national flags.

*Visualization 3: A focus on region differences*

My last visualization is a heatmap showing the average percentage of a selected color in national flags by decade and region, providing a different perspective compared to the previous visualizations. This heatmap visualization is interesting because it allows users to see both temporal and regional variations in the use of specific colors, offering a comprehensive overview of how certain colors have been adopted or discarded over time and across different parts of the world.

The key feature of this visualization is its ability to present data in a matrix format, where each cell represents the average percentage of a specific color in flags for a particular region and decade. By selecting a color from a dropdown menu, users can generate a heatmap that highlights the prevalence of that color in different regions over time. This format makes it easy to identify patterns and anomalies, such as which regions predominantly use a certain color and how its usage has changed over the decades.

The preparation of the heatmap data involves grouping the data by region and decade, then calculating the average percentage of the selected color for each combination. This aggregated data is then displayed in a heatmap using Seaborn, a powerful visualization library in Python. The heatmap is annotated with the exact percentage values, making it easy to read and interpret the data.

One of the main differences between this visualization and the previous ones is the way data is aggregated and presented. While the first visualization provided a snapshot of color distribution and the second showed temporal trends through line plots, this heatmap focuses on both temporal and regional distributions simultaneously. This dual focus allows users to see more granular patterns and correlations, such as how regional preferences for certain colors might align with historical events or cultural shifts.
