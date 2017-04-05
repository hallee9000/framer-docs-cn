Print

Printing allows you to inspect variables on runtime. It works similarly to console.log, only when using print, the output is shown directly within your prototype. Note that you need to use print() in Javascript (but not in CoffeeScript). We will omit these in the rest of the docs.

print "Hello"
# Output: "Hello" 

You can inspect any type of value, and even multiple at the same time.

layerA = new Layer
    x: 10
    y: 20
 
# A single property value 
print layerA.x
# Output: 10 
 
# Multiple values 
print layerA.x, print layerA.y
# Output: 10, 20 

