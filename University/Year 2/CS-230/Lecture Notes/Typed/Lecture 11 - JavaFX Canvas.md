#### THE CANVAS:
- To create a gui in JavaFX, you need to make it up of nodes. These can include: 
	- Button
	- Border
	- Plane
	- Canvas
- The canvas class allows us to create images using simple drawing features 
- We can also combine this class with others to achieve effects like blending.

#### HOW TO CONSTRUCT A CANVAS:
- A canvas is just a visual node
- The image data is stored in a buffer
- This buffer is encapsulated in a GraphicContext object.
- From a canvas object, you can access its GraphicContext
- You can call methods on the GraphicContext to do things like:
	- Set the current stroke colour
		- The colour of lines drawn
	- Set the current fill colour
		- The colour of the inside of the shapes
	- Draw shapes
