We have decided to go with option 1, rotating the screen and controls. With MonoGame everything is treated like a matrix, for example, we can check if game objects have collided with each other using “intersect” to see overlapping of two rectangles. 

Looking at the source code of MonoGame, we see most of the 2D calculates are done using vectors and matrices. Holds position in a vector2, and the whole Camera class inherits from IMovable, and IRotatable. Gives us a good enough hint to figure out where to start with this. 

When creating things in the game world, screenToWorld takes 2 floats and returns Vector transform and inverts the viewMatrix. Scrolling down we can also see functions where we get and set viewMatrices. In our Draw() function I believe we can manipulate, invert matrices, to make it seem like screen is upside down. 

I wasn’t able to see anything in the source code that would also invert the controls as we’re flipping to screen so, I believe it is safe to assume we would be doing that manually. Adding a Boolean variable to see if isInvert correct and we apply the new set of controls for the user
