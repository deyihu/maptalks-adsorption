# maptalks.snap

maptalks snap plugin  
[maptalks.js](https://github.com/maptalks/maptalks.js) version required >= `1.0.0-rc.11`

## Features

* Support Geometry Edit/Draw
* Impressive performance  [perf test](https://maptalks.github.io/maptalks.snap/test/perf.html)

## Install

* NPM

```sh
  npm i maptalks
  # or
  # npm i maptalks-gl
  npm i maptalks.snap
```

* CDN

```html
<script type="text/javascript" src="https://unpkg.com/maptalks/dist/maptalks.min.js"></script>
<script src="https://unpkg.com/maptalks.snap/dist/maptalks.snap.js"></script>
```

## Examples

 [edit Geometry](https://maptalks.github.io/maptalks.snap/test/index.html)<br>
 [draw Geometry](https://maptalks.github.io/maptalks.snap/test/draw.html)<br>
 [custom filtergeometries](https://maptalks.github.io/maptalks.snap/test/filtergeometries.html)<br>
 [filtergeometries from multi layers](https://maptalks.github.io/maptalks.snap/test/multilayerfilter.html)<br>
 [filtergeometries from VT Layer](https://maptalks.github.io/maptalks.snap/test/vt-snap.html)<br>
 [perf test](https://maptalks.github.io/maptalks.snap/test/perf.html)  
 [drag point](https://maptalks.github.io/maptalks.snap/test/dragpoint.html)

 ## API

### Snap

#### constructor(map, options)

 - map
 - options
   - {Number} tolerance `snapTo threshold`

   - {Function } filterGeometries `filter geometries for snap collision. If it is empty, all geometries on the layer where the geometry is located will be obtained`

```js
import {
    Snap
} from 'maptalks.snap';
const snap = new Snap(map, {
    //snapTo threshold
    tolerance: 15,
    // filter geometries for snap collision
    filterGeometries: function() {
        //you can return geometries for snap collision
        return layer.geometries().filter(geo => {
            return geo instanceof maptalks.Polygon;
        })
    }
});

snap.on('snap', (e) => {
    console.log(e);
})

//if you use cdn,Snap Hanging under maptalks namespace
// const snap = new maptalks.Snap(map, {
//     //snapTo threshold
//     tolerance: 15,
//     // filter geometries for snap collision
//     filterGeometries: function() {
//         //you can return geometries for snap collision
//         return layer.geometries().filter(geo => {
//             return geo instanceof maptalks.Polygon;
//         })
//     }
// });
snap.effectGeometry(polygon);
//update options
snap.config({
    tolerance: 18,
    //other opiton params
    ...
})
```

  

#### methods

  + effectGeometry(geometry) ` effect geometry for snap`  
  

```js
snap.effectGeometry(polygon);
snap.effectGeometry(lineString);
```

  + unEffectGeometry(geometry) `remove geometry snap behavior`
  

```js
snap.unEffectGeometry(polygon);
snap.unEffectGeometry(lineString);
```

  + dispose() `dispose Snap`

```js
snap.dispose();
```

#### events

   + snap

   

```js
     snap.on('snap', (e) => {
         console.log(e);
     })
```
