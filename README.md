# Assignment-Analyzing-US-Economic-Data-and-Building-a-Dashboard

import pandas as pd
from bokeh.plotting import figure, output_file, show,output_notebook
output_notebook()

def make_dashboard(x, gdp_change, unemployment, title, file_name):
    output_file(file_name)
    p = figure(title=title, x_axis_label='year', y_axis_label='%')
    p.line(x.squeeze(), gdp_change.squeeze(), color="firebrick", line_width=4, legend="% GDP change")
    p.line(x.squeeze(), unemployment.squeeze(), line_width=4, legend="% unemployed")
    show(p)
    
links={'GDP':'https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/projects/coursera_project/clean_gdp.csv',\
       'unemployment':'https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/projects/coursera_project/clean_unemployment.csv'}
       
 # Type your code here
csv_path = links['GDP']
df = pd.read_csv(csv_path)
df.head()

# Type your code here
csv_path = links['unemployment']
df = pd.read_csv(csv_path)
df.head()

# Type your code here
df[df['unemployment'] > 8.5]

# Create your dataframe with column date
csv_path=links['GDP']
gdp_dataframe=pd.read_csv(csv_path)
x = pd.DataFrame(gdp_dataframe, columns=['date'])
x.head()

# Create your dataframe with column change-current
gdp_change = pd.DataFrame(gdp_dataframe, columns=['change-current'])
gdp_change.head()

# Create your dataframe with column unemployment
unemploy_dataframe= pd.read_csv(csv_path)
unemployment = pd.DataFrame(unemploy_dataframe, columns=['unemployment'])
unemployment.head()

title = "Unemployement stats according to GDP"

file_name = "index.html"

# Fill up the parameters in the following function:
# make_dashboard(x=, gdp_change=, unemployment=, title=, file_name=)
make_dashboard(x=x, gdp_change=gdp_change, unemployment=unemployment, title=title, file_name=file_name)
