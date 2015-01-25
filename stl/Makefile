all: mesh

clean: clean-mesh


mesh:
	cp geometry/nose.stl constant/triSurface/
	surfaceFeatureExtract


clean-mesh:
	rm -rf constant/extendedFeatureEdgeMesh
	rm -f  constant/triSurface/*.stl
	rm -f  constant/triSurface/*.eMesh
