# ==============================================================================
# CSparse CMake File
# ==============================================================================

# objects in library -----------------------------------------------------------
SET(CSPARSE_OBJ
        cs_add.c
        cs_amd.c
        cs_chol.c
        cs_cholsol.c
        cs_compress.c
        cs_counts.c
        cs_cumsum.c
        cs_dfs.c
        cs_dmperm.c
        cs_droptol.c
        cs_dropzeros.c
        cs_dupl.c
        cs_entry.c
        cs_ereach.c
        cs_etree.c
        cs_fkeep.c
        cs_gaxpy.c
        cs_happly.c
        cs_house.c
        cs_ipvec.c
        cs_leaf.c
        cs_load.c
        cs_lsolve.c
        cs_ltsolve.c
        cs_lu.c
        cs_lusol.c
        cs_malloc.c
        cs_maxtrans.c
        cs_multiply.c
        cs_norm.c
        cs_permute.c
        cs_pinv.c
        cs_post.c
        cs_print.c
        cs_pvec.c
        cs_qr.c
        cs_qrsol.c
        cs_randperm.c
        cs_reach.c
        cs_scatter.c
        cs_scc.c
        cs_schol.c
        cs_spsolve.c
        cs_sqr.c
        cs_symperm.c
        cs_tdfs.c
        cs_transpose.c
        cs_updown.c
        cs_usolve.c
        cs_util.c
        cs_utsolve.c
        )

# create static library --------------------------------------------------------
IF(LIBS_STATIC)
    ADD_LIBRARY(csparse_static STATIC ${CSPARSE_OBJ})
    SET_TARGET_PROPERTIES(csparse_static PROPERTIES
                            OUTPUT_NAME csparse
                            CLEAN_DIRECT_OUTPUT 1)
ENDIF(LIBS_STATIC)

# create shared library --------------------------------------------------------
IF(LIBS_SHARED)
    ADD_LIBRARY(csparse_shared SHARED ${CSPARSE_OBJ})
    SET_TARGET_PROPERTIES(csparse_shared PROPERTIES
                            OUTPUT_NAME csparse
                            CLEAN_DIRECT_OUTPUT 1
                            VERSION ${CSPARSE_VERSION})
    INSTALL(TARGETS 
                csparse_shared
            DESTINATION
                lib
            )
ENDIF(LIBS_SHARED)

