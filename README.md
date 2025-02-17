# Main idea

### Write code for the GPU as a regular C# code

```
var motionVectors = positions
    .Zip(normals, speeds)
    .Select((p, n, s) => p + n * s)
    .AsGpu();
```
```
[GPU]
vec3[] GetMotionVectors(){
    var res = new vec3[positions.length];
    for (var id = 0, id < positions.length; id++)
        res[id] = positions[id] + normals[id] * speeds[id];            
    return res;
}

var motionVectors = GetMotioVectors();
```
