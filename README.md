# bsyncpy

## Usage

Simple example
```python
from lxml import etree
from bsync import bsync

# Create a root and set the version attribute
root = bsync.BuildingSync()
root.set('version', '2.2.0')

# Valid element attributes can also be passed in as kwargs
f = bsync.Facilities(bsync.Facilities.Facility(ID='Facility-1'))

# Add the facilities.facility elements to the root
root += f

# write the document to disk
with open('output.xml', 'wb+') as f:
    output = etree.tostring(root.toxml(), pretty_print=True, doctype='<?xml version="1.0" encoding="UTF-8"?>')
    f.write(output)
```

Output
```xml
<?xml version="1.0" encoding="UTF-8"?>
<BuildingSync version="2.2.0">
  <Facilities>
    <Facility ID="Facility-1"/>
  </Facilities>
</BuildingSync>
```