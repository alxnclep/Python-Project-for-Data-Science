### Analyzing Historical Stock/Revenue Data and Building a Dashboard
_Python Project for Data Science (IBM Data Analytics Course Cluster 1, Final Project - Mapua Malayan Digital College)_  


**Learner's Note, yours truly:**

I used VS Code and Skills Network Labs, but as instructed, I have submitted screenshots from my work in Skills Network Labs 
(uploaded to my GitHub profile so I could share the URL in the final peer-graded assignment). Please download the raw file and execute each cell to verify the results. 
As the acting data scientist on this project for a hedge fund, I extracted the profit data for Tesla and GameStop and built a dashboard 
to compare stock prices against the fund’s profits. If there are any issues with my inputs or code, I would greatly appreciate your advice and feedback. Thank you.  

Before the lab provided in the course, an optional reading resource was given — **a summary of GameStop stock vs. Tesla**. I used ChatGPT to create the summary I am including here.  

> **🔹 Summary: Optional: GameStop vs Tesla**  
> **Stock pricing basics:** A company’s stock price usually reflects its profitability and future profit growth. Rising profits typically mean rising stock prices.  
> **Short selling:** Investors can profit from falling stock prices by borrowing and selling shares, then buying them back later at a lower price. Risk: if prices rise instead, losses can be unlimited.  
> **Tesla case:** Many hedge funds shorted Tesla when it wasn’t profitable. Once Tesla became profitable and revenue grew, its stock price surged, proving fundamentals were strong. Short sellers lost money.  
> **GameStop case:** Despite weak profits, retail traders from Reddit’s WallStreetBets coordinated buying, driving the stock price up. The surge wasn’t based on fundamentals, causing hedge funds heavy losses.  
> **Lesson:** Tesla’s growth is fundamentals-driven (sustainable), while GameStop’s spike was sentiment-driven (short-term speculation).  

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

**The graphing function (make_graph) below was provided in the lab**  
- I studied the function and added **text_x=0.05** on fig.update_layout's attribute to center align the Chart Title

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


**Visualization (Tesla and GameStop Historical Share Price and revenue 2009 - June 2021)**  


The dataset was explored using the `make_graph` function provided in the lab.  
Below are the visualizations comparing **Tesla** and **GameStop** stock performance up to June 2021.  

<img width="1312" height="909" alt="Question 5 - Tesla make_graph with title" src="https://github.com/user-attachments/assets/420ede52-fe1c-4c1d-95c7-16fc5d800f57" />  

  
<img width="1312" height="909" alt="Question 6 - GameStop make_graph with title" src="https://github.com/user-attachments/assets/a5711744-1e25-459c-9acd-2bc845627f62" />  


  
**Tesla (2009–2021)**  
- **Stock Price:** Flat until ~2019, followed by a sharp increase peaking in 2020–2021.  
- **Revenue:** Steady year-over-year growth, reflecting Tesla’s production and sales expansion.  
- **Insight:** Tesla’s stock price surge is supported by strong fundamentals, making it a **growth-driven stock**.

  
**GameStop (2004–2021)**  
- **Stock Price:** Stable for years, then sudden spike in early 2021 due to the meme-stock short squeeze.  
- **Revenue:** Seasonal peaks but declining after 2015.  
- **Insight:** The 2021 stock price spike was **market-driven**, not supported by revenue — showing disconnect between fundamentals and price.

---

**Overall Comparison:**  
- Tesla = *Price growth backed by revenue growth.*  
- GameStop = *Price volatility driven by market sentiment, not fundamentals.*  
