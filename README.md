# regional

[![Latest Version](https://img.shields.io/pypi/v/regional.svg?style=flat-square)](https://pypi.python.org/pypi/regional)
[![Build Status](https://img.shields.io/travis/freeman-lab/regional/master.svg?style=flat-square)](https://travis-ci.org/freeman-lab/regional) 

> manipulation and display of spatial regions in python

This package makes it easy to display spatial regions, and is useful when working with geometries, maps, feature extraction, or other spatial analyses. Designed to be small and light-weight, built on [`numpy`](https://github.com/numpy/numpy) and [`scipy`](https://github.com/scipy/scipy), and composes with other modules for image analysis and display.

### install

```bash
pip install regional
```

### example

```python
from regional import one

region = one([[0, 0], [0, 1], [1, 0], [1, 1]])

region.bbox
>> [[0, 1], [0, 1]]

region.center
>> [0.5, 0.5]
```

see the included [notebook](example.ipynb) for a longer example

### usage

#### `region = one(coords)`

constructs a single region 

- `coords`
	- list of coordinates `[[x, y], [x, y], ...]`

![many](https://s3.amazonaws.com/documentation-samples/regional/one.png)

#### `regions = many(list)`

- `list` : 
	- list of regions `[region, region, ...]` or 
	- list of lists of coordinates `[[[x, y], [x, y], ...], [[x, y], [x, y], ...], ...]`

![many](https://s3.amazonaws.com/documentation-samples/regional/many.png)

`one` region and `many` regions have the same [`attributes`](#attributes) and [`methods`](#methods), the only difference is that in the case of `many` regions they are just evaluated once per region

### attributes

#### `region.hull`

convex hull

#### `region.bbox`

rectangular bounding box

#### `region.center`

euclidean center

#### `region.extent`

total region extent

### methods

#### `region.distance(other)`

distance to other region

#### `region.merge(other)`

merge with other region

#### `region.exclude(other)`

exclude other region

#### `region.overlap(other, method)`

compute overlap with other region

#### `region.crop(min, max)`

crop region to bounds

#### `region.inbounds(min, max)`

check whether region falls completely within bounds

#### `region.dilate(size)`

dilate region 

#### `region.outline(inner, outer)`

compute region outline

#### `region.mask(dims, base, fill, stroke, background, value, cmap)`

generate image with regions as colored masks (`value` and `cmap` only for multiple regions)
