# How To: ggplot2

## Prerequisites

- In Jupyter notebook's header:
  ```
  import os
  os.environ['R_HOME'] = '/Library/Frameworks/R.framework/Resources' # put here your own R directory
  %load_ext rpy2.ipython # installed as pip install rpy2
  ```
- Install a new library (after the header):  
  ```
  %%R
  install.packages("ggplot2", repos='http://cran.us.r-project.org', quiet=TRUE) 
  ```
- Start R session (after the header): 
  ```
  %%R -i df -w 6 -h 3 --units in -r 300 # -i is the input (e.g. pandas dataframe)
                                        # -w is the figure width
                                        # -h is the figure height                                       
  library(ggplot2)
  ```  
- Save the plot  
  ```
  %%R 
  ggsave("file_name.pdf", plot = last_plot(), width=3, height=4, dpi=300)
  ```
Note: Never put anything (e.g. comment) before the `%%R`, otherwise `UsageError: Line magic function `%%R` not found.` 

## Data organization  
- The most important thing is to organize data in a dataframe where columns contain the main message to visualize  
- Add columns with variables to group label data with colors, shapes, filling, and size:
  ```
  example:
  
  	value_1	  value_2	  col_for_shape	  col_for_size	 col_for_colors
  0	0.000	    0.000	    yes	            manual         A
  1	1.000	    1.000	    no              automatic      B
  2	1.000	    1.000	    yes             automatic      A
  3	1.000	    0.000	    yes             manual         B
  ...
  ``` 
- In the plot, use the information in the dataframe to determine colors, shapes, filling, and size:   
  ```
  example: 
  
  geom_point(data=df, aes(x=x_values, y=y_values, 
                          size=col_for_size, 
                          shape=col_for_shape, 
                          color=col_for_colors,
                          fill=col_for_colors)) +
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
          geom_point(size=2) + 
          ```    
        - Depending on variable   
          ```
          geom_point(aes(size = variable)) + # aes(size = variable) can be also added to ggplot 
          ```  
        - Proportional to area    
          ```
          scale_size_area() + 
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
  theme (text = element_text(size = 8)) +
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
  
- Flip axis  (= invert `x` and `y`)
  ```
  coord_flip() +
  ```  
  ! `x` and `y` axis properties get inverted too (e.g. `scale_x_continuous` -> `scale_y_continuous`)
  
- Reverse axis
  ```
  e.g.     scale_x_continuous(limits=c(0.5,4.5), breaks=seq(1,4,1),  labels=colnames(df)) + 
  becomes: scale_x_reverse   (limits=c(4.5,0.5), breaks=seq(4,1,-1), labels=rev(colnames(df))) + 
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
  labs(color="new_title")
  labs(size="new_title")
  ```
- Change legend order
  (e.g. point_geom)
  ```
  scale_color_manual(labels = c("F", "A", "I", "R"), # it was "A", "F", "I", "R"
                     breaks = c("F", "A", "I", "R")  # change colors according to new labels
                     ) + 
  ```
- Remove a legend  
  - Option 1: Add the item that creates the legend in `geom_xxx`, but not in the `aes`  
  - Option 2: Add `show.legend = FALSE` in `geom_xxx`, outside `aes`

- Put two legends next to each other:  
  ```
  theme(legend.box = "horizontal")
  ```
