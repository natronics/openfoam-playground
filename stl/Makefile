all: mesh

clean: clean-mesh

mesh: surfaceFeatureExtract

surfaceFeatureExtract:
	cp geometry/nose.stl constant/triSurface/
	surfaceFeatureExtract > log.surfaceFeatureExtract


clean-mesh:
	rm -rf constant/extendedFeatureEdgeMesh
	rm -f  constant/triSurface/*.stl
	rm -f  constant/triSurface/*.eMesh
