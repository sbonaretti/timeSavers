# How To: ggplot2

- In Jupyter notebook's header:
  ```
  import os
  os.environ['R_HOME'] = '/Library/Frameworks/R.framework/Resources' # put here your own R directory
  %load_ext rpy2.ipython # installed as pip install rpy2
  ```
- Install a new library:  
  ```
  %%R
  install.packages("ggplot2", repos='http://cran.us.r-project.org', quiet=TRUE) 
  ```
- Start R session: 
  ```
  %%R -i df -w 6 -h 3 --units in -r 300 # -i is the input (e.g. pandas dataframe)
                                        # -w is the figure width
                                        # -h is the figure height                                       
  library(ggplot2)
  ```


## Geometries  

- **geom_bar**  
  ```
  ggplot(data = df, aes(x = colum_with_labels)) +
         geom_bar(stat="count") + 
  ```
  - Text on bins  
    ```
    geom_text(stat='count', aes(label=..count..), vjust=-1, size = 1.5) +  
    ```
  - Order bins by count
    ```
    ggplot(data = df, aes(x = reorder(colum_name_in_df, colum_name_in_df, function(x)-length(x)))) +
    ```   
  
  **Notes**:
  - Differences between bar charts and histogram: Bar charts provide a visual presentation of categorical data, while histograms are used to plot density of interval (usually numeric) data (see [here](https://stackoverflow.com/questions/14138247/ggplot-geom-bar-vs-geom-histogram))
- **geom_point**
  ```
  ggplot(data = df, aes(x=x_axis, y=caffeine, color=point_color)) + 
        geom_point() + 
  ```
  - Size  
        - Same for all points   
        ```  
        geom_point(size=2)  
        ```    
        - Depending on variable   
        ```
        geom_point(aes(size = variable))
        ```
  
 



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
  scale_x_continuous(limits=c(0, 9000), breaks=seq(0,9000,1000), labels=new_name_of_ticks) +
  scale_y_continuous[same as scale_x_continuous] +
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
theme(plot.title = element_text(size=12, hjust = 0.5)) +
```

### Text  
```
annotate(geom="text", x=6, y=5000, label=paste("Total number of classes: ", dim(df)[1]), color="black", size = 1.5) +
```
where `x` and `y` do not need to be linked to a sample; `paste` concatenates strings and numerical variables   
Note: `geom_text` is much slower

### Legend
- Manipulate one legend (e.g. color)
  ```
  theme(legend.position  = c(0.82, 0.35), # position inside graph
        legend.title     = element_text(size=legend_title_font_size), # title font size
        legend.text      = element_text(size=legend_font_size),       # text font size
        legend.key.size  = unit(0.2,"cm"),                            # distance among legend items
        legend.margin    = margin(0,0,0,0, unit="cm"),                # legend margin
        legend.spacing.y = unit(0.2, "cm")) +                         # spacing between two legends
  labs(color="new_title")                                             # change title (color, alpha, fill)
  ```
- Manipulate two legends (e.g. color and size)  
  ```
  tba
  ```
- Change legend order
  ```
  e.g. point_geom
       scale_color_manual(labels = c("F", "A", "I", "R"), # it was "A", "F", "I", "R"
                          breaks = c("F", "A", "I", "R")  # change colors according to new labels
                          ) + 
  ```
