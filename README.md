# Python Cheat Sheet
         
- [ ] `df1.reindex(columns=df2.columns)`      
updates df1 with all columns in df2.      
new column's are set to NaN.     

- [ ] Graph two columns of dataframe by say, "date" column on x-axis:  
`import matplotlib.pyplot as plt`
`fig = plt.gcf()`
`fig.set_size_inches(50, 20, forward=True)`
`x_pos = np.arrange(len(df["date"].unique())`

`plt.plot(x_pos, df["col1"], lable =f"{col1} in data", color = "blue", linewidth = 3)`
`plt.plot(x_pos, df["col2"], lable =f"{col2} in data", color = "orange", linewidth = 3)`

`xtick_range=np.range(0, len(df["date"].unique()), 10)`
`plt.xticks(xtick_range, df["date"].unique()[xtick_range], rotation = 90)`

`plt.gca().yaxis.offsetText.set_fontsize(50)`
`plt.tick_params(labelsize=50)`

`plt.legend(loc="upper left", prop = {size: 50})`
`plt.title(f"sample graph based on {col1} and {col2} of data", fontdict={"fontsize": 50})`

`plt.grid(True)`
`plt.show()`
`plt.close()`

