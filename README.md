# australian-attitudes-refugees
Choropleths based on Australian electoral divisions and Australian Election Study data

First obtain the shapefile from the AEC website.  Convert shapefile into GeoJSON format.
```
ogr2ogr \
  -f GeoJSON \
  -where "ADM0_A3 IN ('GBR', 'IRL')" \
  electorate_bounds.json \
  COM20111216_ELB_region.shp.shp
```

Convert GeoJSON file to TopoJSON, adopting SORTNAME field as id field and simplifying co-ordinates by 7e-7.
```
topojson \
  -s 7e-7 \
  -o t_aus_bound.json \
  --id-property SORTNAME \
  -- electorate_bounds.json
```
Then obtain the data from the AES ADA archive, sorting by electoral division.
