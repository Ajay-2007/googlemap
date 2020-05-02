```python
with open('apikey.txt') as f:
    api_key = f.readline()
    f.close
```


```python
# import os
# import gmaps

# gmaps.configure(api_key=os.environ["GOOGLE_API_KEY"])
```


```python
gmaps.configure(api_key=api_key)
```


```python
import gmaps
gmaps.configure(api_key=api_key)
```


```python
new_york_coordinates = (40.75, -74.00)
gmaps.figure(center=new_york_coordinates, zoom_level=12)
```


    Figure(layout=FigureLayout(height='420px'))



```python
!jupyter nbextension enable - -py - -sys-prefix widgetsnbextension
```

    Enable an nbextension in frontend configuration.
    
    Usage
        jupyter nbextension enable [--system|--sys-prefix]
    
    Options
    
    -------
    
    
    
    Arguments that take values are actually convenience aliases to full
    Configurables, whose aliases are listed on the help line. For more information
    on full configurables, see '--help-all'.
    
    
    --debug
    
        set log level to logging.DEBUG (maximize logging output)
    
    --user
    
        Apply the operation only for the given user
    
    --system
    
        Apply the operation system-wide
    
    --sys-prefix
    
        Use sys.prefix as the prefix for installing nbextensions (for environments, packaging)
    
    --py
    
        Install from a Python package
    
    --python
    
        Install from a Python package
    --section=<Unicode> (ToggleNBExtensionApp.section)
    
        Default: 'notebook'
    
        Which config section to add the extension to, 'common' will affect all
    
        pages.
    
    To see all available configurables, use `--help-all`
    
    

    Bad config encountered during initialization:
    Invalid argument: '-'
    


```python
!jupyter nbextension enable --py --sys-prefix gmaps
```

    Enabling notebook extension jupyter-gmaps/extension...
          - Validating: ok
    


```python
import gmaps
import gmaps.datasets# Use google maps api
gmaps.configure(api_key=api_key) # Fill in with your API key# Get the dataset
earthquake_df = gmaps.datasets.load_dataset_as_df('earthquakes')#Get the locations from the data set
locations = earthquake_df[['latitude', 'longitude']]#Get the magnitude from the data
weights = earthquake_df['magnitude']#Set up your map
fig = gmaps.figure()
fig.add_layer(gmaps.heatmap_layer(locations, weights=weights))
fig
```


    Figure(layout=FigureLayout(height='420px'))

![](https://github.com/Ajay-2007/googlemap/blob/master/map_1.png)

```python
import gmaps
#configure api
gmaps.configure(api_key=api_key)#Define location 1 and 2
Durango = (37.2753,-107.880067)
SF = (37.7749,-122.419416)#Create the map
fig = gmaps.figure()#create the layer
layer = gmaps.directions.Directions(Durango, SF,mode='car')#Add the layer
fig.add_layer(layer)
fig
```


    Figure(layout=FigureLayout(height='420px'))

![](https://github.com/Ajay-2007/googlemap/blob/master/map_2.png)

```python

```
