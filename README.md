# Python Cheat Sheet
         
## Update df1 with all columns in df2.      
new column's are set to NaN.     
`df1.reindex(columns=df2.columns)`      

## Graph two columns of dataframe by say, "date" column on x-axis:     

```
import matplotlib.pyplot as plt

fig = plt.gcf()

fig.set_size_inches(50, 20, forward=True) 
x_pos = np.arange(len(df["time"].unique()))

plt.plot(x_pos, df[col1], label =f"{col1} in data", color = "blue", linewidth = 3)
plt.plot(x_pos, df[col2], label =f"{col2} in data", color = "orange", linewidth = 3)

xtick_range=np.arange(0, len(df["time"].unique()), 100)
plt.xticks(xtick_range, df["time"].unique()[xtick_range], rotation = 90)

plt.gca().yaxis.offsetText.set_fontsize(50)
plt.tick_params(labelsize=50)

plt.legend(loc="upper left", prop={"size": 20})
plt.title(f"sample graph based on {col1} and {col2} of data", fontdict={"fontsize": 50})

plt.grid(True)
plt.show()
plt.close()
```
## Sort Column Value by SubString
In a CamleCasedString, looking to split by uppercase words first and order in reverse order: 
```
df["order1"] = df["CamleCasedColumn"].apply(lambda x: re.findall("[A-Z][^A-Z]*", x)[::-1][0])
df["order2"] = df["CamleCasedColumn"].apply(lambda x: re.findall("[A-Z][^A-Z]*", x)[::-1][1])
df.sort_values(by=["order1", "order2"], inplace=True)
df = df.drop(columns = ["order1", "order2"])
```

In a patterened string, ordering by specific substring.       
In this example, sorting by email domain vs id names.
```
df 
    name             email
0   Carl    carl@yahoo.com
1    Bob     bob@gmail.com
2  Alice   alice@yahoo.com
3  David  dave@hotmail.com
4    Eve     eve@gmail.com

df = df.set_index('email')
df.reindex(sorted(df.index, key=lambda x: x.split('@')[::-1])).reset_index()

df
              email   name
0     bob@gmail.com    Bob
1     eve@gmail.com    Eve
2  dave@hotmail.com  David
3   alice@yahoo.com  Alice
4    carl@yahoo.com   Carl
```


## Find all rows with NA in any columns 
```
df[pd.isnull(df).any(axis=1)]
```


## Find all non NAN  
```
df[df.notnull().all(1)]
```


## convert all values in a column to upper case and compare: 
```
list(
         map(
                  str.upper, df[df["col_1"].isin(my_list) & (df["col2]=="my_string")]["col1"]
            )
    )
```
