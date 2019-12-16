# Triangulation
WORK IN PROGRESS
Extension of OpenMesh's PolyMesh class which uses ear clipping triangulation.

Currently, OpenMesh's PolyMesh class generates fan triangulations for faces, which is only 
guaranteed to be correct for convex polygons, although it is very fast.
Ear clipping triangulation is guaranteed to work for polygons without holes.
This code is based on the algorithm described in the second edition of
Computational Geometry in C.
If you would like to use the PolyMesh class but would like to generate concave
faces without a lot of work, feel free to steal this code. Use at your own risk.
