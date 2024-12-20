# 04 Bouncy Shapes

This demo contains introductory examples of basic UI, pin joints, instantiation and attribute manipulation.

## UI Sliders

Apart from setting the minium width and height, the UI slider and option dropdown are default.  The value for each is captured in `game.gd`.

```gd
bounciness_slider.value # the current value of the slider
shape_options.selected # the index of the selected item from the drop down (ie. 0, 1, 2)
```

## Instantiation

To instantiate a child scene that is not already present (ie. the bouncy shapes inside the game scene) three steps are required, all of which show up in `game.gd`

```gd
# the child scene is preloaded
var Shape = preload("res://scenes/shape.tscn")

# The child scene is instantiated
var new_shape = Shape.instantiate()

# The child scene is added to the parent.
add_child(new_shape)

```

Note that functions on the child are called _after_ it is added so that the _ready function is fired.


## Attribute Manipulation

Inside the init() function in `shape.gd`, the shape options not being used are pruned :

```
for i in range(shape_options.size()):
  if i == selected_shape:
    selectedOption = shape_options[i]
  else:
    shape_options[i].queue_free()
  ```

  Then the bounciness variable is used to create a new physics material, which is then applied to the new shape.