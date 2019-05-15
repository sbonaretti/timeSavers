# How To: ggplot2

## Axis 

- Label 
  ```
  xlab("x") +
  ylab("y") +
  ``` 

- Size  
  ```
  scale_x_continuous(limits=c(0, 9000), breaks=seq(0,9000,1000)) +
  scale_y_continuous(limits=c(0, 3000), breaks=seq(0,3000,1000)) +
  ```
  where `limits` sets the range and `breaks` sets the ticks

- Font size  
  ```
  theme (axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.3, size = text_size), 
         axis.text.y = [same as axis.text.x]) +  
  ```

