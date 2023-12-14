****************************************************************

# README for the creation of a dashboard using the 'flexdashbaord' package in R: 

# Use case

The following code "Dashboard.Rmd" produces an interactive dashboard, i.e., a standard HTML document that can be deployed on any web server.
We use this dashboard to visualize our findings of the best-performing model when prediciting fast growth for the bisnode data set. According 
to our evaluation metrics (RMSE, AUC, etc.), the best-performing model is the Random forest. Since this is a  “black-box” Machine Learning model,
the interactive dashboard allows us to get a better understanding of how the actual predictions are created and investigate why the Random forest 
model was the best-performing model. 

# Short introduction: Flexdashboard vs. Shiny

Broadly, the flexdashboard library in R allows us to create dynamic dashboards with a combination of narrative text, code, and interactive elements 
while remaining in the "common" markdown environment. It is part of the larger rmarkdown and shiny ecosystems in R, combining the simplicity of rmarkdown 
documents with the interactive capabilities of Shiny apps. Key features are the easy layout creation (combination of rows and columns to organize content),
the responsive design (adapting to different screen sizes etc.), the interactive widgets (i.e., sliders, dropdowns, and buttons, using Shiny elements) and 
the support for multiple output formats, including HTML, PDF, etc. The flexdashbaord differs from a Shiny app in terms of design, interactivity, and complexity.
Overall, the flexdashboard is a more static approach designed for creating reports and dashboards with less emphasis on complex interactivity.

# "Dashboard.Rmd"
Our dashboard (code) is structured as follows: Similar to a rmarkdown file, at the top of the document we have the metadata written in YAML. 
The YAML metadata is used to configure the settings and behavior of the R Markdown document when it is rendered. In addition to a standard markdown file, we 
have to specify here the output as" flexdashboard::flex_dashboard:", set a theme, the orientation (rowwise, columnwise), and the vertical_layout, which is set
to "scrolling" in this case and the navigation bar, which includes, for example, a link to our GitHub repository. In addition, we specify "runtime: shiny" since
we included some Shiny components for interactive visualization of the partial dependence plots, which deploy on a Shiny server or shinyapps.io.

The dashboard has three different pages: Variable Importance, PDP, and Threshold decision. The first one shows three graphs 
variable-importance graphs. First, including all features; second, the ten most important features; and  last, the importance grouped by factors. They are always
shown for the main data set, bisnode, and the two subsets that filter for manufacturing and services. The Second page interactively displays the different 
partial dependence plots again for all three data sets (via a drop-down menu). The last page illustrates the expected loss based on different thresholds again
for all three data sets. 

In order to display the final dashboard, hit the button at the top, "Run Document". 