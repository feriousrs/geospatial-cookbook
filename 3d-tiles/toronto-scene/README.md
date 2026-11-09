# Toronto 3D Tiles sample

A 250 × 250 m sample of a multi-layer 3D urban scene of Toronto, delivered as OGC 3D Tiles with a small CesiumJS viewer. No API key or Cesium ion token is needed.

## Run

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Tick a layer to show or hide it, and click a building or tree to see its attributes.

## Contents

| Layer | Folder | In this sample |
| --- | --- | --- |
| Buildings at LoD 1.3 and 2.2 | `data/buildings` | 19 buildings, one tileset per LoD |
| Roads, sidewalks, curbs and centre lines | `data/transportation` | PBR textures (base colour, normal, occlusion, metallic-roughness) |
| Trees | `data/trees` | 142 instanced trees with attributes |
| Power lines | `data/powerlines` | One stretch of line |
| Poles, street lights and signals | `data/poles` | 68 instanced poles |

## Extent

The sample covers EPSG:2958 (NAD83(CSRS) / UTM 17N):

- Easting 629710 to 629960
- Northing 4833550 to 4833800

Source heights are CGVD2013. The tiles are in Earth-centred coordinates with ellipsoidal heights, as 3D Tiles requires.

## Notes

- Roads and power lines are clipped exactly at the sample edge. Trees and poles are kept if their position is inside it. Buildings are kept whole if their centre is inside it, so a few extend slightly past the edge.
- Attributes are stored in the building and tree tiles only. Roads, power lines and poles have none in their tiles.
- Geometry is compressed with Draco and textures with KTX 2.0 (Basis Universal). Viewers need `KHR_draco_mesh_compression` and `KHR_texture_basisu` support, which CesiumJS has.
- CesiumJS 1.116 loads from the Cesium CDN, so the page needs an internet connection.
