# Influencer Visualization Project
## Project-3-Group-7

## Project Overview and Purpose:

- This project aims to use AI influencers’ data to access their personality analysis and simulate population potential based on real-life youtuber data. The biological analysis starts with demonstrating geographical distribution of all AI influencers. The relationship between educational level and MBTI personality is then observed to understand how MBTI personality impacts influencers’ educational level. Another graphic is presented to reveal the effect of influencers’ personality on lifestyle. We use top 10 influencers subscribers count to demonstrate our data on real-life youtubers and see their geographical distribution around the globe. Then we plotted based on their correlation between average views and likes. Using these data can provide a vision on each AI influencer’s population potential based on real-life youtubers’ views and likes according to their lifestyle.

## Instructions for use:

- Within terminal:
   - **Clone github repo** “git clone https://github.com/AmitaGarad/Project-3-Group-7.git”
   - **Navigate to Project-3-Group-7 directory** “cd .\Project-3-Group-7\”
   - **Run python flask file** “python .\Project3_Flask.py”
   - **Open the link on web browser** “http://127.0.0.1:5000”

## Ethical Considerations:

Use of AI-generated data is an ethical move to present ethical consideration instead of using real data. Real data can cause privacy problems, in the development stage, it is better that we use faked data to simulate the real-life practice. The first subset of the AI-generated data were selected for analyses, however these data are randomly generated by the AI and therefore no biases are introduced due to data selection. Also using Flask can hide back-end analysis and data from the front-end user, which provides data security. The application is built for repeated use in the future. Such as in the human resource industry, HR representatives can use the application to improve the selection standard and filtering process as long as the newest data is imported.

## Data sources:

- [AI Generated Data](https://www.kaggle.com/datasets/anthonytherrien/synthetic-influencer-backstory/)

- [Youtube](https://www.kaggle.com/datasets/ramjasmaurya/top-1000-social-media-channels/)

## Packages Required:

 - **Leaflet**: Javascript library for interactive maps. 
   - [Leaflet Documentation](https://leafletjs.com/)
 - **MarkerCluster**: Leaflet plugin to animate clustering function.
   - [MarkerCluster Documentation](https://leaflet.github.io/Leaflet.markercluster/)
 - **D3**: Javascript library to read in data files.
   - [D3.js Documentation](https://d3js.org/)
- **Chart.js**: Javascript library used to plot. *(NEW PACKAGE)*
   - [Chart.js Documentation](https://www.chartjs.org/)
- **Choropleth Map**: Plotly library that generates choropleth map. *(NEW PACKAGE)*
   - [Plotly.newPlot Documentation](https://plotly.com/javascript/plotlyjs-function-reference/)


## Process/Conclusions:

 - Claire: 
   - Process: Generated geoplot using Leaflet and created an OpenStreetMap base layer and overlay maker layer. Created a getLocationCoordinates function to pull the location names for each influencer and convert them to coordinates by utilizing the Geoapify API tool. Fetched the AI-generated influencer dataset, selected for the first 200 entries (auto-generated dataset randomly generated influencers). Each influencer was plotted on the map, and markerClusterGroup was used to make the markers dynamic as the user zooms in and out of the map. The markers will sum according to region as the map is zoomed out.
   - Conclusions: AI generated influencers from this dataset are assigned to either the United States or Canada. The majority are distributed across the United States, with concentration on the East coast. Although the majority of AI generated influencers are found along the East coast, the state with the highest count is California. New York and Ontario were tied with the second highest number of influencers. These three hotspots are major areas in each country, likely contributing to their selection by the AI generator. Despite concentration in these major areas, the majority of states and provinces did get assigned at least one influencer. So while AI appears to have a tendency to particular regions, other areas did not seem to be neglected.



 - Judith: I focused on the information found in the AI generated influencers dataset. The file was a jsonl file which I imported into the Jupyter Notebook and used Pandas to analyze the file. The jsonl file held 32,890 entries and I took a sample of 2,993 to generate the graphs. I converted the subset into a json file to import into the javascript. The AI dataset had general information about each AI character such as name, age, gender, MBTI Personality, highest education level achieved, lifestyle promoted, and a background. I exclusively focused on the characters MBTI Personality, Education Level, and Lifestyle. In the first graph I wanted to visualize the MBTI Personality with the Lifestyle the character promoted. I wanted to see if the amount of personalities was distributed evenly across the characters or if the majority of characters had a specific personality. In addition, I wanted to see if personality was in conjunction with the character's Lifestyle, would an AI character with the same MBTI Personality promote the same Lifestyle? Initially, I wanted to visualize the data with a scatter matrix, but upon further research I decided to use a spider data chart to visualize the categorical data. In the second graph I wanted to visualize the MBTI Personality with the highest level of education achieved. I wanted to know what educational level was most prevalent and see which MBTI Personality was attributed to that character. It is possible for an AI character to continue developing their education through time, so the data shows a snapshot of the character's life. A stacked bar chart was used to visualize MBTI Personality and Education level. 
After analyzing the file on Pandas I moved to VScode where I created a directory with an html, js, css and the json subset file. In the javascript I fetched the json subset file and passed a promise to read the data. Once the json file was fetched in javascript I created a for loop to go through the data to collect and aggregate the elements. I placed the calculated elements in the trace to be displayed in the graph, and adjusted the layout of the graph. Lastly I referenced the html with Plotly. I placed my work into the group folder and attached my work to a flask.
   - Conclusion: The spider data chart shows that MBTI Personalities are not evenly distributed through the AI characters. There exists a character for each personality, there are 16 MBTI Personalities, yet some personalities show up more frequently than others in this dataset. Also, not all personalities share the same interest in Lifestyle; however, the data shows which MBTI Personality is most likely to promote a specific Lifestyle. For example, it seems that an AI character that produces cooking content will most likely have an ISFP personality. The barchart shows that the majority of the AI characters are in highschool or completed high school, followed by those with a Bachelor's degree or are working on their Bachelors degree.


 - Amita: 
   - Influencer distribution by country: This is designed to fetch data from a server endpoint (/data), process the data, and then use it to create a choropleth map using the Plotly.js library.
 - Here's a detailed explanation of what the code does:
 - Fetch Data:
  - The fetch('/data') function is used to the server endpoint /data.
 - Process Data:
  - The data received from the server is an array of objects, and it is processed using the map function. Each object in the array is transformed into a new object with only the country and count properties, which are extracted from the original object's Country and Count properties, respectively.
 - Create a Choropleth Map:
  - A new object fig is created to define the data and layout for the choropleth map.
  - The text property is set to display a string for each country that includes the country name and the total number of influencers, which will be shown when hovering over the map.
  - The colorscale is set to 'Viridis', which is a color scale ranging from yellow to dark blue.
  - The colorbar is configured with a title to indicate what the colors represent, in this case, the 'Number of Influencers'.
 - Map Layout and Styling:
 - The layout object within fig defines the overall layout and styling of the map.
 - The title property sets the title of the map to 'Influencers count by Country'.
 - Render the Map:
 - Finally, Plotly.newPlot('choroplethMap', fig); is called to render the choropleth map inside an HTML element with the ID choroplethMap using the defined fig configuration.
 - Conclusion:  this code fetches data, formats it to include only the necessary information for the map, and then creates and renders a choropleth map using Plotly.js to visually represent the count of influencers by country. The map is interactive, allowing users to hover over countries to see the number of influencers in each one.


 - Amita: 
   -  YouTube Subscribers Heatmap by category and country: This JavaScript code creates a heatmap using the Plotly library to visualize the number of YouTube subscribers by category and country. 
Here's a detailed explanation of what the code does:
document.addEventListener('DOMContentLoaded', function() { ... }): This event listener ensures that the code inside the function is executed only after the HTML document has been completely loaded and parsed.
fetch('/get_youtube_subscribers_data') ... .then(response => response.json()): This initiates a fetch request to the specified endpoint (/get_youtube_subscribers_data) to retrieve the YouTube subscribers data. The response is then converted to JSON format.
const heatmapData = [{ ... }];: The heatmapData object is created, which includes the z (subscribers data), x (countries), and y (categories) properties, defining a heatmap type chart with a diverging color scale.
Conclusion:  this code fetches YouTube subscribers data, prepares it for visualization as a heatmap, and then uses Plotly to create and display the heatmap in the specified HTML element once the document has finished loading.   


 - Amita: 
   -  Top 10 YouTube Influencer by Subscribers: This JavaScript code is designed to fetch YouTube influencer data from a server endpoint (/get_youtuber_data), process this data to filter and sort it, and then use it to create a grouped bar chart using the Chart.js library.
 - Here's a step-by-step explanation of what the code does:
 - Fetch Data:
  - The fetch('/get_youtuber_data') function is used to asynchronously request YouTube influencer data from the server endpoint /get_youtuber_data.
 - Process Data:
  - The data is then filtered to separate the influencers based on the months of December and November using the filter method.
  - The filtered data for each month is then sorted in descending order by the number of subscribers using the sort method.
  - After sorting, the slice(0, 10) method is used to select the top 10 influencers for each month based on the number of subscribers.
 - Create a Grouped Bar Chart:
  - A new Chart.js chart is created with this context. The chart is of type 'bar', indicating a bar chart.
 - The data for the chart includes:
  - labels for the chart, which are the names of the top 10 YouTubers in December. These names are used as the labels for the grouped bar chart.
  - The options for the chart specify that the index axis should be 'y', meaning the bars will be horizontal. The scales option is set to ensure that the x-axis begins at zero.
 - Error Handling:
  - The .catch(error => ...) part is used to catch and log any errors that occur during the fetch operation or processing of the data.
 - Conclusion:  this code fetches YouTube influencer data from a server, filters and sorts this data to identify the top 10 influencers for December and November based on subscribers, and then creates a grouped bar chart to visually compare the number of subscribers for these influencers across the two months.
s JavaScript code creates a heatmap using the Plotly library to visualize the number of YouTube subscribers by category and country.  


 - Sanja: 
  - total subscribers for each country:  total subscribers for each country, with bars segmented by categories to show the proportion of each category within a country.
Using Jupyter notebook, the September, November, December data is stacked together and then grouped by country to get subscriber counts, category counts, and unique categories.
Then I plot each country’s distribution of categories with stacked bar graphs


 - Sanja: 
  - Combine multiple variables:  Combine multiple variables, such as subscribers, average views, and average likes, where the size and color of the bubbles can represent different metrics.For the same stacked data, using Jupyter notebook, the data is plotted with views as x and likes as y. The data is log2 transformed so that the visualization is easier to see. 
The coloring is also a log2 scaling of comments, and the size of the points is actually a fixed scaling (x0.000001) of subscribers This process is repeated for each of the individual months of the data.In the plots, the x and y labels are falsely suffixed in “(log2)”. This wasn’t necessary since the graph itself is already scaled to display the points properly and the x and y tics are labeled accordingly. Javascripting: 
I found difficulty in converting the python code to javascript, but in general I created functions and looked up a lot regarding how to get the data and and perform conversion accordingly and get plots similar to the jupyter notebook, but using javascript’s plotly instead. 

 
 - Luo:
  - Process: The first step is to use Jupyter Notebook to convert the first 200 AI-Generated data from csv format to json format for Javascript fetch. Then clean the youtuber data from three months respectively and group them by category for information of average views and average likes. Normalize the average views and average likes by dividing them by the highest value and output the data to the Json file for Javascript. Then I created a HTML and Javascript file. On the HTML file, prepare all codes required for Javascript to run. In Javascript, the function of filterDropDown allows AI-generated data to be stored as a button and allows users to input in the textbox to filter names. createInfo function pulls influencers’ bio information based on the user's input button. The createChart function plots the bar and line chart based on the user’s input button.
  - Conclusion: People with lifestyle of Animals & Pets and humor tend to have higher views and likes than majority of others. The category with the lowest views and likes observed is News & Politics, people with respective lifestyles tend to have lower influence as views and likes counts are much lower than other categories. 

- After everyone finishes their analysis, each member’s effort will be consolidated through a single file using Flask. Flask applications can be accessed under the Flask Application folder. Furthermore, the ‘templates’ folder contains all html files and the ‘static’ folder consists of both the ‘css’, ‘js’ and ‘resources’ folders. Folder of ‘js’ contains all js files connecting to the html files; ‘css’ folder contains all files for html styles; resources folder contains all files to access the data.
