# Configure SphereMapping demo build

set(HEADER_FILES include/SphereMapping.h)
set(SOURCE_FILES src/SphereMapping.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_library(Sample_SphereMapping ${OGRE_LIB_TYPE} ${SOURCE_FILES} ${HEADER_FILES})

target_link_libraries(Sample_SphereMapping ${OGRE_LIBRARIES} ${OIS_LIBRARIES})
ogre_config_sample_lib(Sample_SphereMapping)

if (APPLE AND NOT OGRE_BUILD_PLATFORM_APPLE_IOS)
    # Set the INSTALL_PATH so that Samples can be installed in the application package
    set_target_properties(Sample_SphereMapping
       PROPERTIES BUILD_WITH_INSTALL_RPATH 1
       INSTALL_NAME_DIR "@executable_path/../Plugins"
    )
endif()

