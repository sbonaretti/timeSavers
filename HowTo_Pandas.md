# How to: Pandas
 
## Create dataframe

- Create a dataframe  
  ```
  dataframe = pd.DataFrame({'columnName': [list]})
  ```
 
- Put values in pandas dataframe from list  
  ```
  df = pd.DataFrame.from_records(list of lists)
  ```

- Assign column labels
  ```
  df.columns = tags_string
  ```
- Assign name to dataframe
  ```
  df_inHouse.name = "dataframe_name"
  ```
    
  
## Manipulate dataframe
- Start index from 1
  ```
  df.index = np.arange(1,len(df)+1) # start counting rows from 1
  ```
- Move column to first column
  ```
  col = df['column_label']
  df.drop(labels=['column_label'], axis=1, inplace=True)
  df.insert(0,'column_label',col)
  ```
- Change column name 
  ```
  df1.rename (columns={"A" : "first_column", "B": "second_column"}, inplace=True)
  ```


## Display  
- Full dataframe 
  ```
  display(df)
  # or
  df
  ```
- Specific number of rows and columns
  ```
  dataDimension = df.shape # get number of rows
  pd.set_option("display.max_rows",dataDimension[0])
  pd.set_option("display.max_columns",dataDimension[1])
  ```

  
## Query database
- Find cells with a certain value. Four options:  
  ```
  open_repro.query('link_to_open_source_publication != "NaN"').link_to_open_source_publication.count()
  open_repro.where(open_repro.link_to_open_source_publication != "NaN").link_to_open_source_publication.count()
  open_repro.loc[open_repro['link_to_open_source_publication'] != 'NaN'].count()
  open_repro[~open_repro.link_to_open_source_publication.isnull()].count()
  ```  
- Select rows with multiple 
  ```
  b = df1[ (df1["disease"] == "Parkinson's disease") & (df1["organ"] == "frontal lobe") ]
  ```


