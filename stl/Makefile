all: mesh

clean: clean-mesh

mesh: snappyHexMesh

surfaceFeatureExtract:
	cp geometry/nose.stl constant/triSurface/
	surfaceFeatureExtract > log.surfaceFeatureExtract

blockMesh: surfaceFeatureExtract
	blockMesh > log.blockMesh

decomposePar: blockMesh
	decomposePar > log.decomposePar

snappyHexMesh: decomposePar
	mpirun -np 2 snappyHexMesh -parallel < /dev/null > log.snappyHexMesh


clean-mesh: clean-surfaceFeature clean-blockMesh clean-decomposePar clean-log

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

clean-decomposePar:
	rm -rf processor*

clean-log:
	rm -f log.*
