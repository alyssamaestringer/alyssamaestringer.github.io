# PlyBellyButton
In this challenge, I created three different charts using Plotly and javascript to visualize the bacterial data for each user ID. The charts will identify the top 10 bacterial species in each volunteer, or user IDs, belly buttons.

## Bar Chart
We first created a bar chart where we picked out the top 10 bacterial species for each individual's ID. We created a javascript code that parsed through the data to find the OTU IDs, OTU Labels and sample values in order to display the information we wanted. 

## Bubble Chart
We used the same data that we did in the bar chart with OTU Ids, OTU Labels and sample values to build this chart. We just needed to create a new trace for the bubble chart. The code for the trace and layout looks like the following:

```var bubbleData = [{
      x: otu_ids,
      y: sample_values,
      text: otu_labels,
      mode: "markers",
      marker: {
        size: sample_values,
        color: otu_ids,
        colorscale: "Earth"
      }   
    }];
    console.log(bubbleData);

    // 2. Create the layout for the bubble chart.
    var bubbleLayout = {
      title: "Bacteria Cultures Per Sample", 
      showlegend: false,
      xaxis: {
        title: "OTU ID"
      }
    }; 
   ``` 
## Gauge Chart
The gauge chart grabbed different data than we used for the bar and bubble chart. For this one, we wanted the wash frequency to display how many times a user scrubs their belly button per week. I first grabbed the wfreq from the metadata portion of my data file. Here is the code I used for the new gauge trace:

```
var gaugeData = [{
      value: wfreq,
      type: "indicator",
      mode: "gauge+number",
      title: {text: "Belly Button Washing Frequency", font: {size:24}},
      gauge: {
        axis: {range: [0, 10], tickwidth: 1, tickcolor: "darkblue"},
        bar: {color: "black"},
        bgcolor: "white",
        borderwidth: 2,
        bordercolor: "gray",
        steps: [
          {range: [0, 2], color: "red"},
          {range: [2, 4], color: "orange"},
          {range: [4, 6], color: "yellow"},
          {range: [6, 8], color: "lime"},
          {range: [8,10], color: "green"},
        ]
      }
}  
    ];
```

## Updating the web page
The three html elements I updated to customize my webpage were the following:
1. Added an image to the jumbotron
2. Added descriptions beneath each chart
3. Added a gradient background color

