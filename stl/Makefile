all: log.sonicFoam

clean: clean-mesh clean-log


################################################################################
# Mesh:
mesh: log.snappyHexMesh

log.surfaceFeatureExtract:
	cp geometry/rocket.stl constant/triSurface/
	surfaceFeatureExtract > log.surfaceFeatureExtract

log.blockMesh: log.surfaceFeatureExtract
	blockMesh > log.blockMesh

log.snappyHexMesh: log.blockMesh
	snappyHexMesh > log.snappyHexMesh

#log.patchSummary: log.snappyHexMesh
#	patchSummary > log.patchSummary


################################################################################
# Compute
log.sonicFoam: mesh
	sonicFoam > log.sonicFoam


################################################################################
# Cleaning:
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

clean-log:
	rm -f log.*
