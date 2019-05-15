# How To: ggplot2

## Geometries  

- Bar plot  
  ```
  ggplot(data = df, aes(x = colum_with_labels)) +
         geom_bar(stat="count") + 
  ```
  - Text on bins  
    ```
    geom_text(stat='count', aes(label=..count..), vjust=-1, size = 1.5) +
    ```

**Notes**:
- Differences between bar charts and histogram: Bar charts provide a visual presentation of categorical data, while histograms are used to plot density of interval (usually numeric) data (see [here](https://stackoverflow.com/questions/14138247/ggplot-geom-bar-vs-geom-histogram))


## Background  
```
theme_bw() +
```

## Axis 

- Label 
  ```
  xlab("x") +
  ylab("y") +
  ```   
- Label font size  
  ```
  theme (text = element_text(size = 8))+
  ```

- Lengths and ticks
  ```
  scale_x_continuous(limits=c(0, 9000), breaks=seq(0,9000,1000)) +
  scale_y_continuous(limits=c(0, 3000), breaks=seq(0,3000,1000)) +
  ```
  where `limits` sets the range and `breaks` sets the tick step

- Tick text direction, horizontal and vertical adjustment, and font size
  ```
  theme (axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.3, size = 8), 
         axis.text.y = [same as axis.text.x]) +  
  ```

## Title
```
ggtitle("eNanoMapper ontologies") + 
theme(plot.title = element_text(size=12, hjust = 0.5)) 
```


