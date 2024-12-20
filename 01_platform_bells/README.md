# 01 Platform Bells

This demo contains introductory examples of the following: 
	
## Instantiation

When the user clicks anywhere in the scene, the input is captured by [game.gd](scripts/game.gd) and a ball.tscn is spawned at that location via the `instantiate()` function.


## Collisions

[ball.gd](scripts/ball.gd) checks to see if the ball's RigidBody has collided with a platform, and if  it has, calls a method on the platform that it has hit. 

**NOTE** : For ball.gd to report collisions, the following options must be set on the root RigidBody using the Inspector : 

1.  `Solver/Contact Monitoring` 
must be set to `true` 
2. `Solver/Max Contacts` must be set to a number
greater than `0`. 


## Audio

When the ball hits the platform, [platform.tscn](scenes/platform.tcsc) runs `ball_hit()`, which triggers the sound which has been passed (via `@export` to that specific platform. See how this works in the [platform.gd](scripts/platform.gd)


## Animation

`ball_hit()`, also triggers the "bounce" animation on the AnimationPlayer node, which rapidly moves through several rotation keyframes. Open scenes/platform.tscn to see how this works. Select the AnimationPlayer node and then the "Animation" tab.



