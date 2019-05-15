# How To: ggplot2

## Axis 

- Label 
```
xlab("x") +
ylab("y") +
``` 

- Size  
  - with no tick distance
    ```
    scale_x_continuous(limits=c(0, 9000)) +
    scale_y_continuous(limits=c(0, 3000)) +
    ```
  - with tick distance
    ```
    scale_x_continuous(breaks=seq(0,9000,1000)) + 
    scale_y_continuous(breaks=seq(0,3000,1000)) + 
    ```

- Font size  
```
theme (axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.3, size = text_size), 
       axis.text.y = [same as axis.text.x]
       ) 
```

