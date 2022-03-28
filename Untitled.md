#arcgis


# Graphic Object

```js
for (let i = 0; i < data.length; i++){
  graphic = new Graphic({
    geometry: {
      type: "point",
      latitude: data[i].LATITUDE,
      longitude: data[i].LONGITUDE
    },
    attributes: data[i]
  });
  graphics.push(graphic);
}
```



```js

      require([
        "esri/config",
        "esri/Map",
        "esri/views/MapView",
        "esri/widgets/Expand",
        "esri/request",
        "esri/layers/FeatureLayer",
        "esri/layers/support/Field",
        "esri/Graphic"
      ], (
        esriConfig,
        Map,
        MapView,
        Expand,
        request,
        FeatureLayer,
        Field,
        Graphic
      ) => {

//function content
}
```