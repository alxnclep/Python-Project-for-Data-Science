**#Analyzing Historical Stock/Revenue Data and Building a Dashboard**  
_Python Project for Data Science (IBM Data Analytics Course Cluster 1, Final Project - Mapua Malayan Digital College)_  


**Learner's Note, yours truly:**

I used VS Code and Skills Network Labs, but as instructed, I have submitted screenshots from my work in Skills Network Labs 
(uploaded to my GitHub profile so I could share the URL in the final peer-graded assignment). Please download the raw file and execute each cell to verify the results. 
As the acting data scientist on this project for a hedge fund, I extracted the profit data for Tesla and GameStop and built a dashboard 
to compare stock prices against the fund’s profits. If there are any issues with my inputs or code, I would greatly appreciate your advice and feedback. Thank you.  

**Data Used**

- **Tesla Revenue**  
https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/revenue.htm  

- **GameStop Revenue**  
https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html  


**Python Library Used**  
- yfinance
- requests
- warnings
- bs4
- nbformat
- plotly

**The graphing function below was provided in the lab**  
_I added **text_x=0.05** on fig.update_layout's attribute to center align the Chart Title_

> def make_graph(stock_data, revenue_data, stock):
>    fig = make_subplots(rows=2, cols=1, shared_xaxes=True, subplot_titles=("Historical Share Price", "Historical Revenue"), vertical_spacing = .3)  
>    stock_data_specific = stock_data[stock_data.Date <= '2021-06-14']  
>    revenue_data_specific = revenue_data[revenue_data.Date <= '2021-04-30']  
>    fig.add_trace(go.Scatter(x=pd.to_datetime(stock_data_specific.Date, infer_datetime_format=True), y=stock_data_specific.Close.astype("float"), name="Share Price"), row=1, col=1)
>    fig.add_trace(go.Scatter(x=pd.to_datetime(revenue_data_specific.Date, infer_datetime_format=True), y=revenue_data_specific.Revenue.astype("float"), name="Revenue"), row=2, col=1)
>    fig.update_xaxes(title_text="Date", row=1, col=1)  
>    fig.update_xaxes(title_text="Date", row=2, col=1)  
>    fig.update_yaxes(title_text="Price ($US)", row=1, col=1)  
>    fig.update_yaxes(title_text="Revenue ($US Millions)", row=2, col=1)  
>    fig.update_layout(showlegend=False,  
>    height=900,  
>    title=stock,  
>    **title_x=0.5, #Added to center align the title**  
>    xaxis_rangeslider_visible=True)  
>    fig.show()  
>    from IPython.display import display, HTML  
>    fig_html = fig.to_html()  
>    display(HTML(fig_html))  

