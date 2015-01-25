all: mesh

clean: clean-mesh

mesh: blockMesh

surfaceFeatureExtract:
	cp geometry/nose.stl constant/triSurface/
	surfaceFeatureExtract > log.surfaceFeatureExtract

blockMesh: surfaceFeatureExtract
	blockMesh > log.blockMesh

clean-mesh: clean-surfaceFeature clean-blockMesh

clean-surfaceFeature:
	rm -rf constant/extendedFeatureEdgeMesh
	rm -f  constant/triSurface/*.stl
	rm -f  constant/triSurface/*.eMesh

clean-blockMesh:
	rm -f constant/polyMesh/boundary
	rm -f constant/polyMesh/faces
	rm -f constant/polyMesh/owner
	rm -f constant/polyMesh/points
	rm -f constant/polyMesh/neighbour
