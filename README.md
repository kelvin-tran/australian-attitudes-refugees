# Attitudes of Australians towards refugees, by electorate
Choropleths based on Australian electoral divisions and Australian Election Study data

See the results: http://kelvin-tran.github.io/australian-attitudes-refugees/

First obtain the shapefile from the AEC website.  Convert shapefile into GeoJSON format.
```
ogr2ogr \
  -f GeoJSON \
  electorate_bounds.json \
  COM20111216_ELB_region.shp
```

Convert GeoJSON file to TopoJSON, adopting SORTNAME field as id field and simplifying co-ordinates by 7e-7.
```
topojson \
  -s 7e-7 \
  -o t_aus_bound.json \
  --id-property SORTNAME \
  -- electorate_bounds.json
```

Note: the -s flag is used to specify the amount of Visvalingam simplification.  Read more about it by searching topojson simplify.

Then obtain the data from the AES ADA archive, sorting by electoral division.

For further help, see (http://bost.ocks.org/mike/map/, http://bost.ocks.org/mike/simplify/, http://bl.ocks.org/mbostock/4060606)
