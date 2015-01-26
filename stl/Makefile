all: log.sonicFoam

clean: clean-mesh clean-foam clean-log


################################################################################
# Mesh:
mesh: log.snappyHexMesh

log.surfaceFeatureExtract:
	cp geometry/rocket.stl constant/triSurface/
	surfaceFeatureExtract > log.surfaceFeatureExtract

log.blockMesh: log.surfaceFeatureExtract
	blockMesh > log.blockMesh

log.snappyHexMesh: log.blockMesh
	snappyHexMesh -overwrite > log.snappyHexMesh

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
	rm -f constant/polyMesh/owner
	rm -f constant/polyMesh/neighbour
	rm -f constant/polyMesh/cell*
	rm -f constant/polyMesh/face*
	rm -f constant/polyMesh/level*
	rm -f constant/polyMesh/point*
	rm -f constant/polyMesh/refinementHistory
	rm -f constant/polyMesh/surfaceIndex

clean-foam:
	rm -rf postProcessing/

clean-log:
	rm -f log.*
