- Loop over frames in the scene
	- Transform input mesh/shader data from coords + connect → NDArray
	- For functions below use switch with inline else over geometry and shader type to create branchless compile time paths through the rasteriser 
	- prepareSceneGeometry
		- Loop over meshes in the scene
			- Transform coordinates to raster/clip space based on cameras 4x4 transformation matrix
			- Build adaptive hull for high order elems
		- Discard elements that are off screen or are backfacing
		- Count remaining elements in the scene and calculate their axis aligned bounding box
	- sceneTileElemOverlap
		- Loop over meshes in the scene
		- Pass 1: count the number of elements overlapping each tile on the screen → alloc memory for the []overlap Bboxes and the []ActiveTiles
		- Pass 2: populate []ActiveTiles with index into Overlaps
		- Pass 3: populate []OverlapBBox with the bounding box defined by the overlap between the elements bounding box and the tile
	- rasterScene
		- Allocate local scratch buffers for the image and depth buffer by sub-pixel
		- Loop over []ActiveTiles → knows its x/y start/end pixels and where to look in []OverlapBBox to slice out its work. 
		- Loop over []OverlapBBox, knows what mesh it belongs to, what element in that mesh and the x/y min/max of the overlap in screen coors
		- Loop over sub-pixels in the overlap box
		- Invoke Geometry Kernel: Check in/out, calculate weights and depth buffer 
		- Invoke Shader Kernel: Finally invoke shader kernel to fill the sub-pixel with the required value(s)
		- average antit-aliasing back down to normal image size and write to image output buffer.
	- Save image to disk and/or return in memory to user as NDArray

Supported geometry kernels: tri3, tri6, quad4ibi, quad4newtong, quad8, quad9
Supported shader kernels: flat, flat_rgb, texture with rgb u8/u16.
