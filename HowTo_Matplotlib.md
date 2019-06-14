# How to: Matplotlib

- Import  
  ```
  import matplotlib.pyplot as plt
  ```

- Figure size  
  ```
  plt.rcParams['figure.figsize'] = [figureWidth, figLength] # figsize=() seems to be ineffective on notebooks
  fig     = plt.figure() 
  ```

- Subplot 
  ```
  
  fig.tight_layout() # not to overlap subplots
  # cannot call figures inside the for loop because python has a max of 20 figures (nOfImages can be larger)
  
  ax1 = fig.add_subplot(nOfRows,nOfColumns,0)
  
  ax1.set_title(movingRoot + " - Slice: " + str(sliceID[a]))
  
  ```
- Show plot  
  ```
  plt.show()
  ```

# Scatter plot
  ```
  fig     = plt.figure()
  fig, ax = plt.subplots(nrows=1, ncols=1)

  ```
  
  - Errorbar
    ```
    ax.errorbar(x, average, yerr=stdDev, linestyle='None', marker='o')
    ```
  - Ticks  
    ```
    plt.xticks(x) # spacing
    ax.set_xticklabels(imageNames, rotation='vertical')
    ```
  - Axis
    ```
    ax.set_ylabel('thickness [mm]')
    ```



## Images

- Image and mask
  ```
  ax1.imshow(slice_moving_py,   'gray', interpolation=None, origin='lower')                            # image
  ax1.imshow(slice_mask_masked, 'hsv' , interpolation=None, origin='lower', alpha=1, vmin=0, vmax=100) # mask
  ax1.axis('off') # do not show axis ticks and labels
  ```
