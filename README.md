# q3-sof-map-entity-generator
A program that generates entities in the game's map, setting their properties and converts them into .ent file format.

**Things to Note:**
This is software is written in Python 3.
As of today (October 2020) there is no official gui for the python version as I have rewritten my own code and converted the electron app into python source code for further development.
You can contact me directly if you want to use the old APP but I do not recommend using it as the code is old and have some bugs.

# Installation:
Currently to install, you will need to download and install python3 from https://www.python.org/download/releases/3.0/.
Open a new .py file, import both `Points.py` and `ent.py`.
To create a rectangle for example, you will need two corners that are represented by points, Point1 and Point2.
an example would be:
```python
p1 = Point() # not entering any values will default to x=0, y=0 and z=0
p2 = Point(10, 0, 0)
```
This will set two points from (0,0,0) to (10,10,10), also you do not have to worry about the order of which point comes first, or which two corners you have taken, the program will automatically rotate them to be maximum and minimum values.
Now we can use the function "fillRectangle()" this function takes 4 values:
* Point 1 - A point represented by XYZ coordinates.
* Point 2 - A point represented by XYZ coordinates.
* Offset - The offset on each axis entered as a Point constructor (x,y,z) each represent the amount of offset on each axis.
* Outline - A boolean, if you want to hollow out the rectangle set to True and vice versa.
So we can assign one more variable for the offset and add the rectangle:
```python
offset = Point(2,2,2) # offset would be 2 on each axis
Cube = fillRectangle(p1, p2, offset, FALSE)
```
In order to convert your selection to .ent format i wrote the function "toEnt()".
This function takes one main argument and optional properties, the main and first argument would be the array of points that we created in the example above we called "Cube", the properties would be any lines you want your object to consist of.
an example would be:
```python
output = toEnt(Cube, classname="bspmodel", angle="0", modelname="instances/colombia/npc_jump1") # This will fill all the points with a green box object called "npc_jump1"
print(output)
```
