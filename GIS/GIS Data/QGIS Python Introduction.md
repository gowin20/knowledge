# QGIS Python Introduction

Created: Aug 16, 2020 12:09 AM
Last Edited: Feb 17, 2021 1:52 PM
Tags: QGIS
UID: 202008160009

Open the console

```python
layer=iface.activeLayer()
```

- Turns the active layer into

```python
dir(object)
```

- shows you all available methods for any object! Amazing tool

```python
layer.getFeatures()
```

- returns an iterable to all layer features

```python
geom = layerfeature.geometry()
```

- returns a geometry object for layerfeature containing data about the feature

```python
geom.asPoint() #for points
geom.asPolyLine() #for lines
geom.asPolygon() #for polygons
```

- Returns the X and Y coordinates of the point
- returns all coordinates on the line
- returns all coordinates defining a polygon

```python
geom.asPoint().x()
geom.asPolygon.y()
```

- Returns just the x or y coordinates of geom objects

```python
with open('C:\\Users\\gboow\\Documents\\Data\\airports.txt', 'w') as output_file:
	for f in layer.getFeatures():
	  geom=f.geometry()
	  line = '%s, %s, %f, %f\n' % (f['name'], f['iata_code'],
	          geom.asPoint().y(), geom.asPoint().x())
	  unicode_line = str(line) #line.encode('utf-8')
	  output_file.write(unicode_line)
```