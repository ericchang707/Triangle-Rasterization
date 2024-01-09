# Triangle-Rasterization
The goal of this project is for you perform triangle rasterization using the incremental scanline approach. Your code should also interpolate per-vertex colors across the face of the triangles. 
Similar to Project 1A and 1B, you are going to create your own versions of commands that mimic OpenGL commands.  In particular, you will implement the commands Begin_Shape(), Vertex(), and End_Shape(), which will perform triangle rasterization.  You will also implement the Set_Color() command, which allows you to specify either per-triangle or per-vertex color.  Also similar to Project 1A and 1B, you will test your code using test routines that are invoked by pressing keys 1 through 8.  Each such keypress will call a test routine that in turn will draw a triangle using your code.

Here are the functions of the routines that you will write:

Begin_Shape() - Specify that a new triangle is being defined.  It may be that this code does very little, such as setting a vertex counter to zero or initializing a vertex list.

Vertex (x, y, z) - This command specifies the (x, y, z) coordinates of a triangle.  Users of your code will always call this routine exactly three times between a Begin_Shape() and an End_Shape() command.  The code we use to test your commands will always perform exactly three calls to Vertex() between Begin_Shape() and End_Shape(), so you don't need to check for too few or too many vertices.

End_Shape() - Indicates that all the vertices of a triangle have been give, and that the triangle should be rasterized.  This is where the bulk of your code is likely to be.

Set_Color (r, g, b) - Specifies the current color for triangle vertices.  Any vertices that are specified using the Vertex() command will be given the color that was last specified by a Set_Color() command.  The red, green and blue values in this command should be floating point values in the range of 0 to 1.

During triangle rasterization, you will need to set one pixel at a time on the screen as you fill a triangle.  There are two easy ways to accomplish this in Processing.  One way is to use the command set (x, y, color).  The other way is to draw a one-pixel rectangle using rect (x, y, 1, 1).  Either way is fine, but note they require different approaches to specify color.  If you are using rect(), you will want to first use the fill (r,, g, b) command to specify the pixel's color.

As you know, Processing uses (0,0) to refer to the upper left corner of the window.  For this assignment, we are going to treat the lower left corner as (0,0).  This means you will need to flip the y-values of your pixel coordinates before you set the color of a pixel.

Even though the Vertex() command accepts 3D coordinates, we will only be using the x and y coordinates for Part A of this assignment.  Ignore the z values for now.  When two triangles are drawn so that they overlap, the triangle that was drawn last should be entirely visible, and parts of the earlier triangle should be overwritten.  In Part B (not yet!), we will use the z values of each pixel to determine which triangle portions should be visible using the z-buffer algorithm.
